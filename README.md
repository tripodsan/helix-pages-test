# helix-pages-test

## urls

- home: https://helix-pages-test--tripodsan.project-helix.page/index.html
- sub welcome: https://helix-pages-test--tripodsan.project-helix.page/office/sub/welcome.html

## set up subscription

1. get clientId from word2md
2. run `1d login --u helix@adobe.com`
3. resolve your sharelink root: 
   ```
   $ 1d resolve <sharelink from fstab.yaml>
   ```
   copy the `driveId`

5. get the `client-state` secret from the helix-onedrive-listener/secrets/secrets.env :-)   
4. create subscription: 
   ```
   $ 1d sub create \
     /drives/<driveId>/root \
     'https://adobeioruntime.net/api/v1/web/helix-index/helix-services/onedrive-listener@latest/hook?owner=tripodsan&repo=helix-pages-test&ref=master' \
     <client-state>
   ```
   
## set up service bus

1. go to [service bus in azure portal](https://portal.azure.com/#@adobe.onmicrosoft.com/resource/subscriptions/07d1d753-4bfc-4012-9958-35592a40a3fa/resourceGroups/helix-prod/providers/Microsoft.ServiceBus/namespaces/hlxobs/topics) 
2. create new topic: `tripodsan/helix-pages-test/master`
3. go to the topic
4. create a new subscription: helix-index--helix-services--cache-flush_40latest
