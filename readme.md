# 使い方

新規、更新、削除を実行するコマンドを以下に示す。  
aws profile を指定する場合、--profile [プロファイル名] オプションを付加すること  

## 新規

``` bash
$ aws cloudformation create-stack --stack-name myEC2StartStopSchedule --template-body file://ec2-start-stop-schedule.yml --capabilities CAPABILITY_IAM
```

- スタックのリソース（ec2-start-stop-schedule.yml）の中にIAM リソースがあるので、--capabilities オプション指定は必須  
  また、--capabilities オプションに指定する内容は、カスタム名の IAM リソースの指定がないので、CAPABILITY_IAM を指定  
  カスタム名の IAM リソースがある場合、CAPABILITY_NAMED_IAM を指定する必要がある
  ``` bash
  # IAM リソースがあるにもかかわらず --capabilities オプション指定なしだと以下のエラーが発生する
  $ aws cloudformation create-stack --stack-name myEC2StartStopSchedule --template-body file://ec2-start-stop-schedule.yml
  An error occurred (InsufficientCapabilitiesException) when calling the CreateStack operation: Requires capabilities : [CAPABILITY_IAM]
  ```

## 更新

``` bash
$ aws cloudformation update-stack --stack-name myEC2StartStopSchedule --template-body file://ec2-start-stop-schedule.yml --capabilities CAPABILITY_IAM
```

## 削除

``` bash
$ aws cloudformation delete-stack --stack-name myEC2StartStopSchedule
```

## 参考URL

- 【Tips】AWS CLIを使ってAmazon EC2を起動・停止するワンライナーまとめ
  https://dev.classmethod.jp/articles/awscli-tips-ec2-start-stop/
- 【AWS CloudFormation】CAPABILITY_IAM と CAPABILITY_NAMED_IAM どう使い分けたら良いのか
  https://qiita.com/YAMAO_456/items/8104c325c24644c0baeb
- EventBridge Schedulerを使ってEC2を定期起動・停止するCloudFormationテンプレート
  https://dev.classmethod.jp/articles/cloudformation-template-eventbridge-scheduler-ec2-start-stop/

