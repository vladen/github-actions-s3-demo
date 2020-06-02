This project uses GitHub action to deploy static website to AWS S3 bucket configured as a web server.

> assuming that your site has been created with `create-react-app`

## Install dependencies and ensure that `package-lock.json` file exists

`npm install`

## Check if build script successfully runs and emits production version of the web site

`npm run build` should create `build` folder containing `index.html` file and other assets

## Add github action to deploy `build` folder to AWS S3 bucket

copy `.github/workflows/deploy-to-aws.yml` file into your repo

## Explore contents of the workflow file and note that it refers to several secrets

* AWS_S3_BUCKET
* AWS_ACCESS_KEY_ID
* AWS_SECRET_ACCESS_KEY
* AWS_REGION

## Create AWS account

## Create AWS access key

1. Go to [AWS security credentials](https://console.aws.amazon.com/iam/home?region=us-east-1#/security_credentials) to create new access key. Use [this manual](https://docs.aws.amazon.com/general/latest/gr/managing-aws-access-keys.html) for more details.
2. Go to [GitHub](https://github.com) to define `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` secrets in `Settings -> Secrets` of your repository.

## Create AWS S3 bucket

1. Go to [AWS S3 control panel](https://s3.console.aws.amazon.com/s3/buckets) and create a new bucket.
2. Enable static website hosting in properties of newly created bucket.
3. Return to [GitHub](https://github.com) to define remaining secrets. Use
    * name of new bucket as bucket `AWS_S3_BUCKET`
    * and `us-east-1` for `AWS_REGION`.

## Commit and push your local changes to GitHub to trigger new worflow.

1. Go to [GitHub](https://github.com) `Actions -> Deploy to AWS -> Your latest commit -> Job` report
2. Check that all hob steps are successfully executed
3. Enjoy your site up and running on the `http://{your-bucket-name}.s3-website-us-east-1.amazonaws.com` address
