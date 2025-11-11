# Highly-Available-and-Secure-AWS-Dual-Stack-VPC-Design


# 🛡️ تصميم وتنفيذ شبكة VPC مؤمنة وداعمة لـ Dual Stack على AWS

### 📝 نظرة عامة على المشروع (Project Overview)

هذا المستودع يوضح تصميم وتنفيذ شبكة AWS Virtual Private Cloud (**VPC**) تتبع أفضل الممارسات الأمنية ومبادئ **التوفر العالي (High Availability)**. الميزة الأبرز هي دعم الشبكة لتقنية **Dual Stack**، مما يضمن التوافق مع كل من بروتوكولات **IPv4 و IPv6**.

**الهدف الرئيسي:** بناء بنية تحتية آمنة ومُقسمة تفصل بين خوادم الويب (العامة) وقاعدة البيانات (الخاصة).

---

## 🗺️ الهندسة المعمارية (Architecture Diagram)

(هنا يجب أن تضع صورة مخطط الـ VPC الذي قمت بتصميمه)

**[أضف صورة مخطط الـ VPC هنا]**

---

## ✨ المكونات الرئيسية ومزايا التصميم (Key Features)

### 1. التوفر العالي و تقسيم الشبكة

* **مناطق التوافر (Availability Zones):** تم نشر البنية التحتية عبر منطقتي توافر لضمان استمرارية الخدمة في حال فشل منطقة بالكامل.
* **فصل الشبكات:** تقسيم الشبكة إلى:
    * **Public Subnets:** مخصصة لخوادم الويب التي تحتاج إلى الاتصال المباشر بالإنترنت (عبر **Internet Gateway**).
    * **Private Subnets:** مخصصة لقاعدة البيانات (Amazon Aurora) التي يجب أن تظل معزولة وآمنة عن الإنترنت.

### 2. دعم Dual Stack (IPv4 و IPv6)

لضمان الجاهزية للمستقبل وقابلية التوسع، تم تمكين Dual Stack على الـ VPC بالكامل:

* **الاتصال الخارجي الآمن (Egress):** تم توفير مسارات إنترنت آمنة للشبكات الخاصة (Private Subnets):
    * **IPv4:** باستخدام **NAT Gateway** للسماح لحركة الخروج فقط (Outbound traffic).
    * **IPv6:** باستخدام **Egress-Only Internet Gateway** لأغراض مماثلة.

### 3. 🛡️ الدفاع متعدد الطبقات (Multi-Layered Security)

تم تطبيق طبقتين من الأمان الشبكي لضمان حماية قصوى لقاعدة البيانات:

1.  **الطبقة الأولى: السور المحيط (Network ACLs - NACLs)**
    * تعمل كـ **جدار حماية بلا حالة (Stateless Firewall)** على مستوى **الشبكة الفرعية (Subnet)**.
    * تم إعدادها لتسمح فقط بنطاق IP الخاص بخوادم الويب وتطرد أي حركة مرور غير مرغوب فيها.
2.  **الطبقة الثانية: الحارس الشخصي (Security Groups - SGs)**
    * تعمل كـ **جدار حماية ذكي (Stateful Firewall)** على مستوى **المثيل (Instance)**.
    * **قاعدة حاسمة:** تم تقييد الوصول لمنفذ قاعدة البيانات بحيث يُسمح بالاتصال فقط من **Security Group** الخاصة بخوادم الويب (SG-to-SG Rule).

---

## 🖼️ دلائل التنفيذ (Implementation Proofs)

(يرجى استبدال هذه النصوص بروابط أو صور الإعدادات الخاصة بك)

* **[صورة قواعد الـ NACL]**
* **[صورة قواعد الـ Security Group]
# 🛡️ Highly Secure Dual-Stack VPC Design and Implementation on AWS

### 📝 Project Overview

This repository showcases the design and implementation of an AWS Virtual Private Cloud (**VPC**) following security best practices and **High Availability** principles. A key feature is the network's support for **Dual Stack**, ensuring compatibility with both **IPv4 and IPv6** protocols.

**Core Objective:** To build a secure, segmented infrastructure separating web servers (public) from the database (private).

---

## 🗺️ Architecture Diagram

(Please embed your VPC architecture diagram image here)

**[Embed your VPC Diagram image here]**

---

## ✨ Key Components and Design Features

### 1. High Availability and Network Segmentation

* **Availability Zones (AZs):** The infrastructure is deployed across two Availability Zones to ensure service continuity against single-zone failures.
* **Network Segmentation:** The VPC is divided into:
    * **Public Subnets:** For Web/Application Servers that require direct internet access (via **Internet Gateway**).
    * **Private Subnets:** Dedicated to the database instances (Amazon Aurora), which must remain isolated and secure from the internet.

### 2. Dual Stack Support (IPv4 & IPv6)

To ensure future-readiness and scalability, Dual Stack is enabled across the VPC:

* **Secure Egress Traffic:** Safe outbound internet paths are provided for the Private Subnets:
    * **IPv4:** Using a **NAT Gateway** to allow only outbound traffic for updates and patches.
    * **IPv6:** Using an **Egress-Only Internet Gateway** for the same purpose.

### 3. 🛡️ Multi-Layered Security

Two primary network security layers are enforced to ensure maximum protection for the database:

1.  **Layer 1: Network Perimeter (Network ACLs - NACLs)**
    * Acts as a **stateless firewall** at the **Subnet level**.
    * NACLs are configured to only allow traffic originating from the correct Web Subnet IP range, dropping unwanted traffic immediately.
2.  **Layer 2: Personal Guard (Security Groups - SGs)**
    * Acts as a **stateful firewall** at the **Instance level**.
    * **Critical Rule:** Access to the database port (e.g., 3306) is restricted to only allow connections originating from the **Security Group** of the Web servers (SG-to-SG Rule).

---

## 🖼️ Implementation Proofs

(Please replace these placeholders with links or images of your actual AWS configurations)

* **[NACL Rules Screenshot]**
* **[Security Group Rules Screenshot]**
* **[Route Tables Screenshot]**
* **[صورة جداول التوجيه (Route Tables)]**

---
