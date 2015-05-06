# Ansible CloudWatch Logs Role
An Ansible role for forwarding log files to [CloudWatch](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/WhatIsCloudWatchLogs.html).

You can opt to forward one or many log files to CloudWatch; each file may use a different datetime format and belong to a different log group,

## Prerequisites
`aws-cloudwatch-logs` assumes you are using an official Ubuntu AMI, and it obviously only makes sense to run within EC2. Sorry if this doesn't fit your use case.

## Usage
Include the `aws-cloudwatch-logs` role in your playbook yml like this:

    - role: aws-cloudwatch-logs
      logs:
        - file: /var/log/syslog
          format: "%b %d %H:%M:%S"
          group_name: syslog
        - file: /var/log/my_cool_log
          format: "%b %d %H:%M:%S"
          group_name: my-cool-log
