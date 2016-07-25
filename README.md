#### ehjwt
######Creating JWTs (JSON Web Tokens) in Node
```
npm install -g crypto
```
then test
```
> let header = {typ:'JWT',alg:'HS256'}
undefined
> header = new Buffer(JSON.stringify(header)).toString('base64')
'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9'
> let payload = {iat:Date.now(),iss:'nodebotanist',username:'ke'}
undefined
> payload = new Buffer(JSON.stringify(header)).toString('base64')
'ImV5SjBlWEFpT2lKS1YxUWlMQ0poYkdjaU9pSklVekkxTmlKOSI='
> let sign = crypto.createHmac('sha256','ke')
undefined
> key=header+'.'+payload
'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.ImV5SjBlWEFpT2lKS1YxUWlMQ0poYkdjaU9pSklVek
kxTmlKOSI='
> sign.update(key)
Hmac { _handle: {}, _options: undefined }
> key=sign.digest('base64')
'HoGUVGJO8+Vfy/bTn+wyySlQbVS+DZIq5DRXjsvkKhM='
> let token = header +'.'+payload+'.'+key
undefined
> token
'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.ImV5SjBlWEFpT2lKS1YxUWlMQ0poYkdjaU9pSklVek
kxTmlKOSI=.HoGUVGJO8+Vfy/bTn+wyySlQbVS+DZIq5DRXjsvkKhM='
```
to verify
```
jwt.io
```
