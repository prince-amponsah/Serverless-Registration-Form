# AWS Serverless Application with Lambda, API Gateway, and DynamoDB

This guide walks through creating a serverless web application using **AWS Lambda**, **API Gateway**, and **DynamoDB**.

## Prerequisites

- **AWS Account**
- **Basic knowledge of AWS services**
- **Python** (for the Lambda function)

---

## Steps to Create the Serverless Application

### 1. Create a DynamoDB Table

1. Go to the **DynamoDB console**.
2. Create a new table with the following configuration:  
   - **Primary/Partition Key**: `Email`

### 2. Set Up IAM Role for Lambda

1. Navigate to the **IAM console** and create a new role for Lambda with the least-privilege model.
2. Attach the following permissions:
   - **DynamoDB Access** (to allow the Lambda function to interact with the table)
   - **CloudWatch Logs Access** (to monitor logs)

### 3. Create the Lambda Function

1. In the **Lambda console**, create a new function.
2. Select **Python** as the runtime.
3. Assign the IAM role created in the previous step to the Lambda function.

### 4. Configure API Gateway

1. Go to the **API Gateway console**.
2. Create a new **API**.
3. Add a **Resource** to serve as the endpoint for incoming requests.

#### Create a POST Method

1. For the resource, create a **POST method**.
2. Select the integration type and link it to the Lambda function.
3. Click **Save**.
4. **Enable CORS** on the resource:
   - Select the resource.
   - Enable CORS with default options.

### 5. Deploy the API

1. Click **Deploy API**.
2. Create a new stage (e.g., `dev`, `prod`).
3. Note the **Invoke URL** generated after deployment.

### 6. Connect the API to Your Frontend

1. Open your `script.js` file.
2. Update the `API_URL` with the **Invoke URL** from API Gateway.
3. Open `index.html` and fill out the form.

### 7. Verify the Integration

1. Submit the form and check the DynamoDB table to see if the data is saved.
2. If the data isn’t saving, review your configurations and ensure all steps are completed correctly.

---

## Folder Structure Example

```plaintext
project-folder/
│-- Frondend/index.html
│-- Frondend/script.js
│-- Lambda/lambda_function.py
```


Credit: https://github.com/yeshwanthlm

## Notes

- Ensure CORS is enabled for API Gateway to allow cross-origin requests.
- Use **CloudWatch Logs** for debugging any issues with the Lambda function.

