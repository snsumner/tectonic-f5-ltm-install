# Using F5 BigIP LTM with Tectonic

When installing Tectonic on bare metal or VMware you have to bring your own load balancer whereas with cloud provider such as AWS, Tectonic automatically setup a load balancer (e.g. AWS ELB) for you. During the Tectonic installation you need to provide the Master DNS which resolves to any master node and Tectonic DNS which resolves to any worker nodes for Ingress. For evaluation purposes some will simply create a DNS entry that points to each node but ideally you want to utilize a load balancer. The purpose of this document is to explain how to setup F5 BigIP LTM to work with Tectonic in this configuration.

## Overview

### Prerequisites

- F5 BigIP LTM 10.x or higher
  - Should be in same datacenter we you plan to install Tectonic
- Tectonic installer
- VMware or Bare metal environment
- Pre-allocated IP addresses for cluster and pre-created DNS records

## DNS and IP address allocation

Installation of Tectonic requires using static allocation of IP Addresses for Bare metal or VMware installation.

Prior to the start of setup create required DNS records. Below is a sample table of 2 master nodes (self-hosted etcd) and 2 worker nodes.

| Record | Type | Value |
|------|-------------|:-----:|
|tectonic.scottsumner.net | A | 192.168.1.91 |
|api.scottsumner.net | A | 192.168.1.92 |
|master-01.scottsumner.net | A | 192.168.1.110 |
|master-02.scottsumner.net | A | 192.168.1.111 |
|worker-01.scottsumner.net | A | 192.168.1.112 |
|worker-02.scottsumner.net | A | 192.168.1.113 |

In this example the virtual IP for console traffic will be 192.168.1.91, DNS resolvable at tectonic.scottsumner.net and the virtual IP for API traffic will be 192.168.92, DNS resolvable at api.scottsumner.net

## Create F5 LTM Pools

## Create F5 Virtual Servers 
