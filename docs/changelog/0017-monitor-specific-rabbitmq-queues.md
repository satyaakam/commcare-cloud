# 17. Only monitor specific RabbitMQ queues

**Date:** 2019-02-27

**Optional per env:** _only required on some environments_


## CommCare Version Dependency
This change is not known to be dependent on any particular version of CommCare.


## Change Context
Datadog RabbitMQ monitoring restricts the number of queues it
can monitor to 200. To avoid hitting this limit on large
scale deployments we limit the queues being monitored to only
the primary queues.

## Details
This will result in only the queues listed in the config file
being monitored by Datadog.

## Steps to update
1. Update datadog integrations on the RabbitMQ machine:
```bash
commcare-cloud <env> deploy-stack --limit=rabbitmq --tags=datadog_integrations
```