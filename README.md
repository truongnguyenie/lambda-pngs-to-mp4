# lambda-pngs-to-mp4

Convert a slew of pngs into an mp4

# Usage

Invoke this function like any lambda function, as documented in the aws sdk.

- [JavaScript](http://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/Lambda.html#invoke-property)
- [Ruby](http://docs.aws.amazon.com/sdkforruby/api/Aws/Lambda/Client.html#invoke-instance_method)
- [PHP](http://docs.aws.amazon.com/aws-sdk-php/latest/class-Aws.Lambda.LambdaClient.html#_invokeAsync)
- [Python](http://boto.readthedocs.org/en/latest/)
- OR on the function's "edit" tab via amazon's interface
- OR via the AWS CLI

# Payload

## required

- `srcBucket` - S3 bucket with the pngs
- `srcKeys` - Array of keys to download from the srcBucket
- `dstBucket` - S3 bucket to dump the mp4
- `dstKey` - Key to upload the mp4 to

## optional

- `srcUrl` - URL for an `endcard` - this file will be downloaded and built into
  a `video-endcard.mp4` file with 45 frames. NOTE: this param will override the
  srcBucket and srcKeys params, but the function will be treated as 'invalid' if
  either of those is null. Not ideal, should be fixed. For now, I set
  `srcBucket` and `srcKeys` to `"none"` when using this param.
