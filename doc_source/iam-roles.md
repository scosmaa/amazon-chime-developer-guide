# Example IAM roles<a name="iam-roles"></a>

For users to access the Amazon Chime SDK messaging features, you must define an IAM role and policy to provide credentials to users when they sign in\. The IAM policy defines the resources that users can access\.

The examples in this section provide basic policies that you can adapt to suit your needs\. For more information about how policies work, see [Making SDK calls from a backend service](call-from-backend.md)\. 

This example shows a policy for developers building applications using Amazon Chime SDK messaging\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "chime:CreateAppInstance",
                "chime:DescribeAppInstance",
                "chime:ListAppInstances",
                "chime:UpdateAppInstance",
                "chime:DeleteAppInstance",
                "chime:CreateAppInstanceUser",
                "chime:DeleteAppInstanceUser",
                "chime:ListAppInstanceUsers",
                "chime:UpdateAppInstanceUser",
                "chime:DescribeAppInstanceUser",
                "chime:CreateAppInstanceAdmin",
                "chime:DescribeAppInstanceAdmin",
                "chime:ListAppInstanceAdmins",
                "chime:DeleteAppInstanceAdmin",
                "chime:PutAppInstanceRetentionSettings",
                "chime:GetAppInstanceRetentionSettings",
                "chime:PutAppInstanceStreamingConfigurations",
                "chime:GetAppInstanceStreamingConfigurations",
                "chime:DeleteAppInstanceStreamingConfigurations",
                "chime:TagResource",
                "chime:UntagResource",
                "chime:ListTagsForResource"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

This example shows a policy that allows users to access the Amazon Chime SDK user actions\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": "chime:GetMessagingSessionEndpoint",
            "Effect": "Allow",
            "Resource": "*"
        },
        {
            "Action": [
                "chime:CreateChannel",
                "chime:DescribeChannel",
                "chime:DeleteChannel",
                "chime:UpdateChannel",
                "chime:ListChannels",
                "chime:ListChannelMembershipsForAppInstanceUser",
                "chime:DescribeChannelMembershipForAppInstanceUser",
                "chime:ListChannelsModeratedByAppInstanceUser",
                "chime:DescribeChannelModeratedByAppInstanceUser",
                "chime:UpdateChannelReadMarker",
                "chime:CreateChannelModerator",
                "chime:DescribeChannelModerator",
                "chime:ListChannelModerators",
                "chime:DeleteChannelModerator",
                "chime:SendChannelMessage",
                "chime:GetChannelMessage",
                "chime:DeleteChannelMessage",
                "chime:UpdateChannelMessage",
                "chime:RedactChannelMessage",
                "chime:ListChannelMessages",
                "chime:CreateChannelMembership",
                "chime:DescribeChannelMembership",
                "chime:DeleteChannelMembership",
                "chime:ListChannelMemberships",
                "chime:CreateChannelBan",
                "chime:DeleteChannelBan",
                "chime:ListChannelBans",
                "chime:DescribeChannelBan",
                "chime:Connect"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:chime:us-east-1:{awsAccountId}:app-instance/{appInstanceId}/user/{appInstanceUserId}",
                "arn:aws:chime:us-east-1:{awsAccountId}:app-instance/{appInstanceId}/channel/*"
            ]
        }
    ]
}
```

This example shows a policy that gives users minimal access to Amazon Chime SDK user actions\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": "chime:GetMessagingSessionEndpoint",
            "Effect": "Allow",
            "Resource": "*"
        },
        {
            "Action": [
                "chime:ListChannels",
                "chime:DescribeChannel",
                "chime:ListChannelMembershipsForAppInstanceUser",
                "chime:DescribeChannelMembershipForAppInstanceUser",
                "chime:ListChannelsModeratedByAppInstanceUser",
                "chime:DescribeChannelModeratedByAppInstanceUser",
                "chime:SendChannelMessage",
                "chime:GetChannelMessage",
                "chime:ListChannelMessages",
                "chime:Connect"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:chime:us-east-1:{awsAccountId}:app-instance/{appInstanceId}/user/{appInstanceUserId}",
                "arn:aws:chime:us-east-1:{awsAccountId}:app-instance/{appInstanceId}/channel/*"
            ]
        }
    ]
}
```

This example shows a policy for establishing a websocket connection for an `AppInstanceUser`\. For more information about websocket connections, see [Using websockets to receive messages](websockets.md)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
   {
     "Effect": "Allow",
     "Action": [
             "chime:Connect"
            ],
     "Resource": [
             "arn:aws:chime:us-east-1:{awsAccountId}:app-instance/{appInstanceId}/user/{appInstanceUserId}"
         ]
      }
   ]
}
```