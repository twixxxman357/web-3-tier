# 🏗️ AWS 3‑Tier Architecture (Terraform)

This repository contains Infrastructure‑as‑Code (IaC) for deploying a **highly available, secure, and scalable 3‑tier architecture on AWS using Terraform**.

The design follows AWS best practices with dedicated **Web**, **Application**, and **Database** tiers, spread across multiple Availability Zones for fault tolerance.

---

## 📸 Architecture Diagram


## 🔧 Architecture Overview

### **1. Web Tier (Public Subnets)**

* Hosts public‑facing **EC2 instances**
* Scaled and distributed using an **Elastic Load Balancer (ELB)**
* Internet traffic enters through an **Internet Gateway (IGW)**
* Web servers access the App tier through internal load balancing

### **2. Application Tier (Private Subnets)**

* Contains backend **EC2 application servers**
* Only accessible from the Web tier
* No direct internet exposure
* Connects securely to the database tier

### **3. Database Tier (Private Subnets)**

* Powered by **Amazon Aurora (Primary + Read Replica)**
* Deployed in private subnets
* Application servers interact with Aurora over secure connections
* Read replica improves scalability for read‑heavy workloads

---

## 🛡️ Key Security Features

* Public access limited strictly to ELB
* EC2 instances in App and DB tiers have **no direct internet access**
* **Security Groups** control traffic flow between tiers
* **Subnets isolated** by purpose (public vs private)
* Multi‑AZ for high availability

---

## 📁 Repository Structure

```
/terraform
  ├── modules
  │   ├── vpc
  │   ├── ec2
  │   ├── alb
  │   ├── rds
  │   └── security-groups
  ├── environments
  │   ├── dev
  │   └── prod
  ├── variables.tf
  ├── main.tf
  ├── outputs.tf
  └── README.md
```

---

