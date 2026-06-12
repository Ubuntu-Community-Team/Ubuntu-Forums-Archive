---
title: "Installing mysql-server"
date: 2009-09-25
forum: General Help
---

### Post by r_s on 2009-09-25
When I try to install MySQL-server using synaptic manager it returns me an error message which is..

E: /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb: subprocess pre-installation script returned error exit status 1

I cannot understand why this error message is displayed ???

---

### Post by porchrat on 2009-09-25
Are you running Ubuntu 9.04?

Is it a fresh install of MySQL or are you upgrading?

Looks like quite a few people are experiencing problems like this on 9.04 (mostly the 64bit though by the looks of it, not the 32bit which I assume you are running by the looks of that package name).

---

### Post by r_s on 2009-09-25
Yes I am running ubuntu 9.04 and its a fresh install of MySQL.

---

### Post by karlson on 2009-09-25
> **r_s said:**
> When I try to install MySQL-server using synaptic manager it returns me an error message which is..

E: /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb: subprocess pre-installation script returned error exit status 1

I cannot understand why this error message is displayed ???

Check to see if any mysql packages are already installed.

Had the same problem so had to remove everything mysql before installing the server.

---

### Post by rakete on 2009-09-25
[xampp]("http://www.apachefriends.org/en/xampp-linux.html") could be an alternative if you are not up to set up a productive server enviroment... it is set up in minutes and provides mysql...

---

