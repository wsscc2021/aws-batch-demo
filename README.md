
Source Repository: https://github.com/angelarw/aws-batch-monte-carlo-workshop

Updated version and fixed a few bugs:
- Updated python version: 3.6 -> 3.9
- Updated ibrary:
  - pandas 0.23.4 -> 1.3.4
  - boto3 1.9.25 -> 1.19.5
  - pandas-datareader 0.7.0 -> 0.10.0
  - yahoo-finance 0.0.22 -> yfinance 0.1.64
- Fixed a few source code due to above element.

---
1. Simulator build to container
```bash
git clone https://github.com/wsscc2021/aws-batch-demo.git
cd aws-batch-demo/src
docker build . -t monte-carlo-simulator:latest
```

2. Testing for simulator run
```bash
docker run -t  monte-carlo-simulator:latest
```
```plaintext
running 10 iterations
[*********************100%***********************]  1 of 1 completed
skipping s3 upload as no bucket is specified
```

3. ECR Push
```bash
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com
docker tag monte-carlo-simulator:latest <account-id>.dkr.ecr.<region>.amazonaws.com/monte-carlo-simulator:latest
docker push <account-id>.dkr.ecr.<region>.amazonaws.com/monte-carlo-simulator:latest
```
