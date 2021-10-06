# github-actions-configure-aws-credentials-playground 

learn [aws-actions/configure-aws-credentials](https://github.com/aws-actions/configure-aws-credentials)

## Demo

```sh
PROFILE=admin
REGION=us-east-1
STACK_NAME="configure-aws-credentials-playground"

aws cloudformation deploy \
    --profile "${PROFILE}" \
    --region "${REGION}" \
    --stack-name "${STACK_NAME}" \
    --template-file sample-role.yaml \
    --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" \
    --parameter-overrides GitHubOrg=pfeilbr \
        RepositoryName=github-actions-configure-aws-credentials-playground \
#        OIDCProviderArn="arn:aws:iam::529276214230:oidc-provider/vstoken.actions.githubusercontent.com"

# run workflow manually
gh workflow run default.yml

# list runs
gh run list --workflow=default.yml

# show run details 
gh run view <run-id>

# delete stack
aws cloudformation delete-stack \
    --profile "${PROFILE}" \
    --region "${REGION}" \
    --stack-name "${STACK_NAME}"
```

successful workflow run with `aws sts get-caller-identity`

![](https://www.evernote.com/l/AAGFdh9yCjpGyacSCdALNi1MrcBA7claSrAB/image.png)

## Resources

* [aws-actions/configure-aws-credentials](https://github.com/aws-actions/configure-aws-credentials)
* [AWS federation comes to GitHub Actions](https://awsteele.com/blog/2021/09/15/aws-federation-comes-to-github-actions.html)
* [benkehoe/github-actions-boto3-demo: Demonstrate how GitHub OIDC token getting should be included in boto3](https://github.com/benkehoe/github-actions-boto3-demo)