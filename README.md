# PayPay-AnalyticSystem
An approach to design a Google Analytic like backend system. We need to provide Google Analytic like services to our customers.


# Data Fetching
Though not the backend things still need to considered JavaScript agents(e.g-websockets) that collects metrics required for the analytics. Uses MetricsAPI to communicate with the backend.

# Load Balancer

HAProxy - A high availability load balancer and proxy server for TCP and HTTP-based applications that spreads requests across multiple servers.
- This ensure running system with minimum downtime. 
- Support IPv6 and UNIX socket
- Deflate & Gzip compression
- Health-check
- Source-based session stickiness
- Inbuilt statistics reporting

# Backend
The idea for backend development would be to choose Golang for implementing this for low resource requirement (memory), as we need to scale horizontally.

# Application server 
Which hosts application to serve http, http2.
Micro-service architecture would be good enough for scalable development and keeping high performance in mind, server side programming would be with Golang(for less footprint than others & also works well with modern web components).
Servers can be aggregated together for request and response handling.
Specific request redirection to specific server can be achieved by HAProxy.


# Analytics & Processing
Context based request caching would be great idea to have, because we can keep track of users most searched queries and mark the context out of queries to deliver the result faster.

Data aggregation based on time-metrics for each client. Message processing bus(like Kafka) will be highly useful and can be distributed across multiple servers and datacenters in order to handle large amounts of requests.
Metrics from message bus to create analytics that can be leveraged to the customer. It needs to re-calculated frequently to include recent metrics. Aggregator can be later expanded region wise to keep services fast and flexible.

# Data Base
MongoDB - It supports both relational and NoSQL. As it is schema free it can support changes/updates(unstructured data) of DB structure with the growth/change in application. Full index support for high performance, replication, and fail-over (a fault-tolerance measure achieved through redundancy) for high, real-time availability of data.
