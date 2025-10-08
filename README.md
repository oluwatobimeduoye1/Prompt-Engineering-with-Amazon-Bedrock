# Prompt-Engineering-with-Amazon-Bedrock
Deploy a single-page application with Amazon S3, AWS Lambda, and Amazon API Gateway so that users can interact with large language models within Amazon Bedrock Experiment with different prompt engineering techniques to improve LLM responses in the app.


This solution implements a serverless single-page web application to assist customers with personalized prompt recommendations powered by generative
Al.

- Customers access the application through Amazon CloudFront, a highly distributed, fast, and secure content delivery network.
- Amazon CloudFront caches and serves the static content hosted on Amazon Simple Storage Service (Amazon S3), stored in an 53 bucket. CloudFront provides low latency, offloads traffic from the origin S3 bucket, and improves performance and cost.
- Amazon API Gateway acts as the front door for the single-page app hosted on Amazon S3. API Gateway helps developers create, publish, and maintain secure APIs at any scale.
- AWS Lambda provides the environment for the serverless generation of dynamic content, and it interfaces with Amazon Bedrock. The tuning of prompt engineering techniques is also done in Lambda by altering and enhancing the original customer prompts with additional context.
- Amazon Bedrock provides access to high-performing foundation models (FMs) from leading Al companies such as Anthropic, Cohere, Stability Al, and Amazon.
- Amazon Bedrock offers a serverless experience and access to cutting-edge generative Al capabilities while maintaining privacy, security, and responsible Al practices.
- Using Amazon Sagemaker Studio and a SageMaker Studio notebook, data scientists experiment and refine the prompt templates for the application.
- A Studio notebook provides the ideal place to test and experiment, helping data scientists and developers build, train, and deploy machine learning (ML) models.
- Studio notebook is fully managed, comes with pre-installed ML frameworks and libraries, is integrated with AWS services, and provides collaboration features for teams working on Al projects.

<img width="904" height="532" alt="Screenshot 2025-10-07 at 22 33 16" src="https://github.com/user-attachments/assets/f2fc55e2-2d0a-4872-a61a-c4112cd4b43b" />


### AWS Services Used
- **Amazon S3** – Hosts the static web application.  
- **Amazon CloudFront** – Distributes and caches content globally for low-latency access.  
- **Amazon API Gateway** – Acts as the secure API interface between the SPA and backend logic.  
- **AWS Lambda** – Executes serverless code to call Bedrock models and process user prompts.  
- **Amazon Bedrock** – Provides access to foundation models like Anthropic Claude, Cohere, and Stability AI.  
- **Amazon SageMaker Studio** – Enables experimentation and optimization of prompt engineering techniques.

---

## 🎯 Project Objectives

- Deploy an **AWS Lambda function** that invokes Amazon Bedrock models.  
- Configure **Amazon API Gateway** to integrate securely with Lambda.  
- Deploy and test a **single-page application (SPA)** hosted on S3 and distributed through CloudFront.  
- Use **SageMaker Studio notebooks** to refine prompt templates and evaluate model response quality.

---

## 💡 Business Benefits

### 1. **Scalable and Cost-Efficient AI Deployment**
Serverless architecture ensures **pay-per-use scalability**, eliminating infrastructure management while reducing costs.

### 2. **Accelerated AI Adoption**
Organizations can experiment with multiple **foundation models** in Amazon Bedrock without worrying about model training or hosting complexity.

### 3. **Improved Customer Personalization**
LLM-powered recommendations (e.g., media or retail personalization) enhance engagement and retention through data-driven interaction.

### 4. **Rapid Experimentation with Prompt Engineering**
Using **SageMaker Studio**, data scientists can fine-tune prompts (Zero-shot, Few-shot, Chain-of-Thought) and instantly observe output variations.

### 5. **Enterprise-Grade Security**
Integration with **API Gateway**, **IAM roles**, and **CloudFront HTTPS** ensures secure access, data privacy, and compliance.

---

## ⚙️ Prompt Engineering Techniques Used

| Technique | Description | Example Use Case |
|------------|--------------|------------------|
| **Zero-Shot Prompting** | Direct task execution without examples. | Generate TV show recommendations based on user metadata. |
| **Few-Shot Prompting** | Provide example Q&As or interactions. | Build a conversational assistant. |
| **Chain-of-Thought (CoT)** | Encourage step-by-step reasoning. | Estimate target audience size or reasoning tasks. |

---

## Example Use Case

A **media and entertainment company** uses the app to:
- Generate personalized TV show recommendations for users based on demographics and interests.  
- Use **SageMaker Studio** to test and refine prompt styles for improved recommendation accuracy.  
- Deploy the app globally via CloudFront for consistent, low-latency user experience.

---

## Technical Implementation Steps (Summary)

1. **Enable Model Access** in Amazon Bedrock (e.g., *Nova Pro* model).  
<img width="1179" height="417" alt="Screenshot 2025-10-07 at 22 48 51" src="https://github.com/user-attachments/assets/4819c519-8fb9-45f9-b4ef-e7d17139924b" />

2. Experiment in **Bedrock Playground** to create system prompts.         
<img width="1466" height="730" alt="Screenshot 2025-10-07 at 22 52 45" src="https://github.com/user-attachments/assets/c9ef257e-098d-43c6-8423-9ec615697ec4" />
Using the Amazon Bedrock playground, you can experiment with various FMs without having to write any code.  ( we can create system prompts and also prompt the FM ) 

3. Open **SageMaker Studio** and run the Jupyter notebook to test prompt variations. 
SageMaker Studio provides a unified, web-based visual interface where developers and data scientists can perform the entire ML workflow, from data preparation and
model building to training, debugging, deployment, and monitoring.

4. Package Lambda code:
   ```bash
   zip lambda_function.zip lambda_function.py
   aws lambda update-function-code --function-name invoke_bedrock --zip-file fileb://lambda_function.zip
<img width="1414" height="688" alt="Screenshot 2025-10-07 at 23 30 32" src="https://github.com/user-attachments/assets/b2e77d21-127b-4f4b-a0f3-a9d030a14a3f" />

    Replace API endpoint in index.html:

const API_URL = "<YOUR_API_GATEWAY_ENDPOINT>";

Upload the SPA to S3 and deploy via CloudFront:

WEB_BUCKET=$(aws s3 ls | grep www- | awk '{ print $3 }')
aws s3 cp index.html s3://$WEB_BUCKET/

Access the deployed web app via the CloudFront distribution domain.
<img width="1351" height="777" alt="Prompt Engineering with Amazon Bedrock" src="https://github.com/user-attachments/assets/b805f012-7ae6-4db9-9324-7171e88661c1" />
<img width="1470" height="956" alt="Prompt Engineering with Amazon Bedrock" src="https://github.com/user-attachments/assets/857c4f84-bd3c-450d-bbfe-74a3d93b944b" />


Key Outcomes

- Implemented a fully serverless generative AI pipeline on AWS.

- Experimented with multiple prompt optimization strategies.

- Deployed a global, secure, low-latency SPA for LLM interaction.

- Learned Bedrock integration, Lambda orchestration, and API Gateway best practices.

- Strengthened expertise in AI + Cloud integration workflows.


## Author
**Oluwatobi Isaac Meduoye** 
