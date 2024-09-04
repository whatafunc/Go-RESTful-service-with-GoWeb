This Go App runs on both Win and Mac

The app stays running (ie it should be like our previous one) and it listens the calls to it on a certain port,
i.e. it works as a RESTful API server.

The first function to add to it will be to communicate with the iOS app. 
A tiny iOS test app has a “Connect” button and then connects to this app and says “Success” if it connects . 

That app code repo iOS mobile client is  at https://github.com/block888dev/iOS-client-for-a-GoWeb-RESTful-service

Step1: this is just a “hello world” type of program to begin with  and the test iOS app that connects to this server and handshakes or something. Of course when we achieve step 1 there will be more steps

test: 
```
curl -i -X GET http://192.168.0.108:9090/
HTTP/1.1 200 OK
X-Custom-Header: Goweb
Date: Fri, 31 May 2024 07:23:42 GMT
Content-Length: 17
Content-Type: text/plain; charset=utf-8

Hello from GOLANG
```

step 2 (after we get “hello world” working), will be iOS sending a input.txt to  Server2.exe
test: 
```
curl -i -X POST -H "Content-Type: multipart/form-data" -F "file=@Input.txt" http://192.168.0.108:9090/upload
HTTP/1.1 200 OK
X-Custom-Header: Goweb
Date: Fri, 31 May 2024 06:50:44 GMT
Content-Length: 58
Content-Type: text/plain; charset=utf-8

File uploaded successfully{"e":["File processed"],"s":200}
```

Step3  Server copies input.txt to c:\bb and runs some app to process this text file

Step4  

Step5  

Step6  


Extra features may be considered:
- limit the response from GO app and makie it only JSON
- log all events to mysql db
- add protection agains all calls and any client so that only the filtered ones gets through
- remove goweb framework's test REST API calls and keep just the needed ones

*Here is how the app gets compiled:
example: env GOOS=target-OS GOARCH=target-architecture go build package-import-path
real cmd:      
```GOOS=windows GOARCH=386 go build -o Server2.exe main.go```
 or
```GOOS=windows GOARCH=amd64 go build -o Server2.exe main.go```

PS: for clients:

Things to consider when building a RESTful API with PG SQL Database:
- how much data you have and would you need a pagination?
- which libs do you prefer to use for db connection and also for the REST
API?
- do you need to setup an encrypted connection to db or just the default is
OK?
- do you need docker-compose to be provided or just Golang code?
- do you need any Unit tests done?