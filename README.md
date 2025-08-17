# Real-Time-Leaderboard
Learn event-driven architecture with DynamoDB Streams.
# Scenario:
You have a game app storing scores in DynamoDB. Every time a score is added or updated, a Lambda function should process it and update a leaderboard.

**Tasks:**

1. Enable DynamoDB Streams (NEW_IMAGE).
2. Create a Lambda function triggered by the stream.
3. In the Lambda, log the updated score and maintain a top-5 leaderboard in another DynamoDB table.
4. Test by inserting/updating scores in the GameScores table.

**Step 1: Create the GameScores Table**
  Go to AWS Console → DynamoDB → Tables → Create table.

<img width="1043" height="476" alt="image" src="https://github.com/user-attachments/assets/e0d02266-4bd8-4e18-9dd7-568c1fd8a427" />
<img width="1051" height="472" alt="image" src="https://github.com/user-attachments/assets/2790e019-47b2-4757-9a0e-2c375d015662" />
<img width="1073" height="253" alt="image" src="https://github.com/user-attachments/assets/e9b0cdbc-1c6a-4ed7-8fc4-964b97edeacb" />
<img width="1350" height="478" alt="image" src="https://github.com/user-attachments/assets/b5beedc8-ad86-488d-906f-222044255815" />


**Step 2: Insert Sample Player Scores**
  Open the GameScores table → Explore table items → Create item.

<img width="1034" height="279" alt="image" src="https://github.com/user-attachments/assets/cf240a18-03d3-4f9b-b2cc-02ba2602db63" />
Repeat for more players

**Step 3: Create the Leaderboard Table**
  Go back to DynamoDB → Tables → Create table.

<img width="1010" height="453" alt="image" src="https://github.com/user-attachments/assets/9d9faf24-71db-4e3e-ae7e-125929106ff6" />
<img width="1045" height="242" alt="image" src="https://github.com/user-attachments/assets/102cf6bf-731a-456a-a61d-e28ac13748b8" />

**Step 4: Create a Lambda Function**
  Go to AWS Console → Lambda → Create function.
<img width="1331" height="434" alt="image" src="https://github.com/user-attachments/assets/af87b626-f619-4791-8c2c-9e051c0aebc5" />
<img width="1347" height="246" alt="image" src="https://github.com/user-attachments/assets/061cb826-973f-41b7-a4ed-64da91dbb2b7" />

Create a new role with AmazonDynamoDBFullAccess.
<img width="1075" height="446" alt="image" src="https://github.com/user-attachments/assets/7270613c-e05e-4d85-bf7c-896e81b77447" />

After creation, paste in the Lambda code
<img width="975" height="512" alt="image" src="https://github.com/user-attachments/assets/86cc1b7c-7e64-4ff9-84b2-740a8defd0b6" />

**Step 5: Connect DynamoDB Stream to Lambda**
  Go back to the GameScores table.
  Choose Triggers → Create trigger.
  Select your Lambda function
<img width="1329" height="493" alt="image" src="https://github.com/user-attachments/assets/e5f7bf8a-1550-4149-b7a6-afbc2c7faa30" />

**Step 6: Test the Flow**

Add or update player scores in the GameScores table (manually via console).
<img width="1340" height="501" alt="image" src="https://github.com/user-attachments/assets/7b27df6e-211d-4460-836c-31d59ed6324a" />

Wait a few seconds for the Lambda to run.
Go to the Leaderboard table → Explore items.



