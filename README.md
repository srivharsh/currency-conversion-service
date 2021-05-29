# currency-conversion-service

**Microservices with Spring Boot and Spring Cloud**

In this project we've two different Microservices created using spring-boot. Below is the list of the implementations that we've done.

1) We've established communication between Microservices.
2) Centralized Microservice Configuration with Spring Cloud Config Server
3) Simplified communication with other Microservices using Rest Template and Feign REST Client
4) Implemented the client side load balancing with Ribbon
5) Implement dynamic scaling using Eureka Naming Server and Ribbon

What we'll have is.

1) **Currency-exchange-service:** This will give the currency conversion rate between two currencies and the port on which the application is running. We've exposed a GET Api which will give us an output like

![image](https://user-images.githubusercontent.com/84402285/120076509-79d3a000-c0c3-11eb-9c85-7a7d563e9d05.png)

Here we've exposed our API on port **8000** and we'll launch the same service again on port **8001** parallely.

2) The currecy-exchange-service will fetch the data from the **h2 database**. A sample database structure would look something like

![image](https://user-images.githubusercontent.com/84402285/120076583-db940a00-c0c3-11eb-8b44-0bd64bac422b.png)

3) **Currency-conversion-service:** This service will convert the one currency to the other based on the user input. We've exposed a GET Api which will give us an output like

![image](https://user-images.githubusercontent.com/84402285/120076637-3463a280-c0c4-11eb-9042-60c9b7d3bf78.png)

Here we've exposed our API on port **8100**

4) **Eureka-naming-server:** This service will have the configurations for both the above services and the above services will interact with this service. 

![image](https://user-images.githubusercontent.com/84402285/120076785-f74be000-c0c4-11eb-9793-5e217fd64c88.png)

5) These instances will be registered with Eureka and the we'll have the Eureka hosted on port **8761**. A simple Eureka UI will look something like
![image](https://user-images.githubusercontent.com/84402285/120076843-409c2f80-c0c5-11eb-9b04-76b4ce36729e.png)

6) Overall this is what we've created.

![image](https://user-images.githubusercontent.com/84402285/120076956-a4265d00-c0c5-11eb-95c0-85e570c9399b.png)

Once the whole configuration is done Eureka will dynamically handle load to be sent on the running instances. For instance if we remove the CurrencyExchangeService2, no request will be sent to that service. We can confirm the same by verifying the port. 


