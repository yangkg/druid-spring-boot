# Druid Spring Boot Starter

[![Build Status](https://api.travis-ci.org/drtrang/druid-spring-boot.svg?branch=master)](https://www.travis-ci.org/drtrang/druid-spring-boot)
[![Coverage Status](https://coveralls.io/repos/github/drtrang/druid-spring-boot/badge.svg?branch=master)](https://coveralls.io/github/drtrang/druid-spring-boot?branch=master)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.drtrang/druid-spring-boot/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.github.drtrang/druid-spring-boot)
[![License](http://img.shields.io/badge/license-apache%202-brightgreen.svg)](https://github.com/drtrang/druid-spring-boot/blob/master/LICENSE)

Druid Spring Boot Starter 将帮助你在 Spring Boot 中使用 Druid。


## 依赖
```xml
<dependency>
    <groupId>com.github.drtrang</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.0.1</version>
</dependency>
```


## 配置
### 简单配置
在引入依赖的情况下，只需如下配置即可使用 Druid：

```yaml
spring:
  datasource:
    driver-class-name: org.h2.Driver
    url: jdbc:h2:file:./samples
    username: root
    password: 123456
```

### Druid 连接池
Druid Spring Boot Starter 会将以 `spring.datasource.druid` 为前缀的配置注入到 DruidDataSource，且 DruidDataSource 中的所有参数均可自定义，没有配置的将使用 DruidDataSource 的缺省值。

```yaml
spring:
  datasource:
    druid:
      initial-size: 1
      min-idle: 1
      max-active: 10
      validation-query: SELECT 1
      test-while-idle: true
      test-on-borrow: false
      test-on-return: false
      pool-prepared-statements: true
      max-open-prepared-statements: 20
      use-global-data-source-stat: true
```

### Druid 高级特性
Druid Spring Boot Starter 添加了 Druid 的大部分特性，如 StatFilter、WallFilter、ConfigFilter、WebStatFilter 等，其中 StatFilter 默认打开，其它特性默认关闭，需要手动开启。

同样，每个特性的参数均可自定义，具体参数可以用 IDE 的自动提示功能或者阅读 Druid 的 [Wiki](https://github.com/alibaba/druid/wiki/%E9%A6%96%E9%A1%B5) 查看。

```yaml
spring:
  datasource:
    druid:
      slf4j:
        # 开启 Slf4jFilter
        enabled: true
      wall:
        # 开启 WallFilter
        enabled: true
      web-stat:
        # 开启 Web 监控
        enabled: true
      stat-view-servlet:
        # 开启监控展示
        enabled: true
```

### 配置示例
[application.yml](https://github.com/drtrang/druid-spring-boot/blob/master/druid-spring-boot-samples/src/main/resources/application.yml)


## 演示
[druid-spring-boot-samples](https://github.com/drtrang/druid-spring-boot/tree/master/druid-spring-boot-samples) 演示了 Druid Spring Boot Starter 的使用方式，可以作为参考。   


## 作者信息
QQ：349096849<br>
Email：donghao.l@hotmail.com