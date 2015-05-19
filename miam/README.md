[Mim](http://miam.codenize.tools/)

# install

```
$gem install bundle
$bundle install
```

# export

 ユーザー、ロール、グループを全てまとめたファイル
```
$miam -e -o IAMfile 
Export IAM to `IAMfile`
```

ユーザー、グループ、ロール、インスタンスプロファイルを分ける

```
$miam -e --split
Export IAM
                                                                                                                                                                                                             ᗧ 100%
  write `./users.iam`
  write `./groups.iam`
  write `./roles.iam`
  write `./instance_profiles.iam`
  write `IAMfile`
```

それぞれのユーザー、グループ、ロール、インスタンスプロファイルを分ける

```
$miam -e --split-more
Export IAM
                                                                                                                                                                                                             ᗧ 100%
  write `./users/abcuser.iam`
  write `./groups/beanstalk_full.iam`
  write `./groups/cloudtrail-builder.iam`
  write `./groups/read_only_group.iam`
  write `./groups/root_user.iam`
  write `./roles/S3_Access.iam`
  write `./roles/S3_web.iam`
  write `./roles/WebIdentityDynamoDBRole.iam`
  write `./roles/aws-elasticbeanstalk-ec2-role.iam`
  write `./roles/dynamodb.iam`
  write `./instance_profiles/S3_Access.iam`
  write `./instance_profiles/aws-elasticbeanstalk-ec2-role.iam`
  write `./instance_profiles/dynamodb.iam`
  write `IAMfile`
```

# apply

dry-run
```
$miam -a --dry-run
Apply `IAMfile` to IAM (dry-run)
                                                                                                                                                                                                             ᗧ 100%
Create Group `beanstalk_full` > Policy `beanstalk_full-TOSHIHIROCK-PROJECT` (dry-run)
  {"Version"=>"2012-10-17",
   "Statement"=>
    [{"Effect"=>"Allow",
      "Action"=>
       ["elasticbeanstalk:*",
        "ec2:*",
        "elasticloadbalancing:*",
        "autoscaling:*",
        "cloudwatch:*",
        "s3:*",
        "sns:*",
        "cloudformation:*",
        "rds:*",
        "sqs:*",
        "iam:CreateRole",
        "iam:CreateInstanceProfile",
        "iam:GetUser",
        "iam:ListInstanceProfiles",
        "iam:ListRoles",
        "iam:PassRole"],
      "Resource"=>"*"}]} (dry-run)
Delete Group `beanstalk_full` > Policy `beanstalk_full-TOSHIHIROCK-TEST-PROJECT` (dry-run)
No change
```

apply
```
$miam -a --dry-run
Apply `IAMfile` to IAM
                                                                                                                                                                                                             ᗧ 100%
Create Group `beanstalk_full` > Policy `beanstalk_full-TOSHIHIROCK-PROJECT`
  {"Version"=>"2012-10-17",
   "Statement"=>
    [{"Effect"=>"Allow",
      "Action"=>
       ["elasticbeanstalk:*",
        "ec2:*",
        "elasticloadbalancing:*",
        "autoscaling:*",
        "cloudwatch:*",
        "s3:*",
        "sns:*",
        "cloudformation:*",
        "rds:*",
        "sqs:*",
        "iam:CreateRole",
        "iam:CreateInstanceProfile",
        "iam:GetUser",
        "iam:ListInstanceProfiles",
        "iam:ListRoles",
        "iam:PassRole"],
      "Resource"=>"*"}]}
Delete Group `beanstalk_full` > Policy `beanstalk_full-TOSHIHIROCK-TEST-PROJECT`

```

apply(no change)
```
$miam -a --dry-run
Apply `IAMfile` to IAM
                                                                                                                                                                                                             ᗧ 100%
No change
```
