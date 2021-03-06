# feignInterceptorExample

An example application to show how to set authorization header to feign requests. 

If you keep your authorization token in your `SecurityContext` then you're not able to read `SecurityContext` using `feign.RequestInterceptor` because 
`SecurityContext` and `HystrixRequestContext` are on different threads. For more information, 
you should read this [blog post](https://jfconavarrete.wordpress.com/2014/09/15/make-spring-security-context-available-inside-a-hystrix-command/).


## Running the application
To demonstrate setting and using authorization header, I decided to retrive user data from github api
which requires basic authentication. So firstly, you have to generate token 
with your [github account](https://github.com/settings/tokens). By the way, you don't need to select 
any scope. Then, generated token and username must be set
as below in your application.yml:
```
github:
  username: username
  token: generated-token
```

After setting properties, in the project root directory
```
mvn spring-boot:run
```
login credentials are:

> username: *give-any-username*

> password: *1*
