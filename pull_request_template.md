## Please answer the following questions
1. Did you fulfilled every requirements from the Jira task description? (Y/N)

2. Did you record the time spent on the Jira task? (Y/N)

3. Did you created/updated and passed unit test cases for the changes? (Y/N, if not please explain why)

4. Did you finish manual test for the changes? (Y/N, if not please explain why)

---

## Changes in Environment Variables (Optional)
**Add**

```STRIPE_PUBLISHABLE_KEY=pk_test_51IH52vI2l506XUR7P8FvCSZDoHxk2Xr8bZxgzDEhR8BE3EtaIH81aSRWz3xwdtDsKn1NFu3CwXnJ9QZKZ9u4ndY200Dlz6DifK```

**Remove**

```WASABI_ACCESS_KEY_ID, WASABI_SECRET_ACCESS_KEY, WASABI_REGION```

---

## Migration Steps (Optional)
**Before running in local/dev environment,**

1. Execute the following queries in the MongoDB collection
```
...
```

**Before running in staging/prod environment,**

1. Create a bucket in aws in format "sendtext_[stage]"
2. execute the following queries in the MongoDB collection
```
...
```

---

## Manual Test Steps


**To test creating text template**

1. Run Outdating Queries -> Template -> Create
```
{
    "companyId": "624efd6eef1eeed33e9a5557",
    "inputs": {
        "name": "test_create_template",
        "category": "MARKETING",
        "language": "en",
        "components": [
            {
                "type": "BODY",
                "text": "Hi 😄"
            }
        ]
    }
}
```


**To test creating media template**
1. Get S3 Media ID 
    - Outdating Queries -> Media -> Create Presigned URL For Upload
    - Upload to Presigned URL (ref. https://medium.com/@aidan.hallett/securing-aws-s3-uploads-using-presigned-urls-aa821c13ae8d)

2. Run Outdating Queries -> Template -> Create

```
{
    "companyId": "624efd6eef1eeed33e9a5557",
    "inputs": {
    "name": "test_upload_image",
    "category": "MARKETING",
    "language": "en",
    "components": [
        {
            "type": "HEADER",
            "format": "IMAGE",
            "example": {
                "headerHandle": [
                    MEDIA_ID
                ]
            }
        },
        {
            "type": "BODY",
            "text": "Hi 😄"
        }
    ]
}
}
```
