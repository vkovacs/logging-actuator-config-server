# Prerequisites

A rabbitmq broker running on the default port on localhost.

docker run -d --hostname my-rabbit --name some-rabbit -p 15672:15672 -p 5672:5672 rabbitmq:3-management
docker run -e POSTGRES_PASSWORD=deb.deb -e POSTGRES_DB=config-db -p 5432:5432 -d postgres:latest

In case of using jdbc backend the following table:
```
create table properties (
    application varchar(255),
    profile varchar(255),
    label varchar(255),
    key varchar(255),
    value varchar(255)
)
```

an example line looks like this:
```
insert into properties values ('logging', 'default', null, 'message', 'apple')
```

# Documentation
https://cloud.spring.io/spring-cloud-config/reference/html/#_quick_start

# Cloud config bus
https://medium.com/swlh/spring-cloud-config-bus-auto-refresh-properties-for-clients-d18fa4c036cb

# Trigger config change

```
"you can trigger a change notification by POSTing to /monitor with form-encoded body parameters in the pattern of path={name}. Doing so broadcasts to applications matching the {name} pattern (which can contain wildcards)."
```
![call_monitor_endpoint.png](call_monitor_endpoint.png)

https://cloud.spring.io/spring-cloud-config/multi/multi__push_notifications_and_spring_cloud_bus.html

# Profiles:
* To use config server by a file system backend use profile: `native`
* To use config server by a jdbc backend use profile: `jdbc`