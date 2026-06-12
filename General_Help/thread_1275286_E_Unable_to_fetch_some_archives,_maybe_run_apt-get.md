---
title: "E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"
date: 2009-09-25
forum: General Help
---

### Post by talphp on 2009-09-25
what the #%$# is that? :O

```

server2@server2:~$ sudo sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom
The following NEW packages will be installed:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common libapr1 libaprutil1 libpq5
0 upgraded, 7 newly installed, 0 to remove and 56 not upgraded.
Need to get 1703kB of archives.
After this operation, 6054kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Err http://il.archive.ubuntu.com jaunty-updates/main libapr1 1.2.12-5ubuntu0.1
  Could not resolve 'il.archive.ubuntu.com'
Err http://il.archive.ubuntu.com jaunty/main libpq5 8.3.7-1
  Could not resolve 'il.archive.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main libapr1 1.2.12-5ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main libaprutil1 1.2.12+dfsg-8ubuntu0.3
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main apache2-utils 2.2.11-2ubuntu2.3
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main apache2.2-common 2.2.11-2ubuntu2.3
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main apache2-mpm-worker 2.2.11-2ubuntu2.3
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main apache2 2.2.11-2ubuntu2.3
  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.12-5ubuntu0.1_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://il.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.7-1_i386.deb  Could not resolve 'il.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.2.12+dfsg-8ubuntu0.3_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.11-2ubuntu2.3_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2.2-common_2.2.11-2ubuntu2.3_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-worker_2.2.11-2ubuntu2.3_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.11-2ubuntu2.3_all.deb  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by credobyte on 2009-09-25
```
sudo apt-get update && sudo apt-get install --fix-missing apache2

```

---

### Post by michy99 on 2009-09-25
Those particular servers may be down temporarily.

---

### Post by talphp on 2009-09-25
how can i change the servers path? (i have no GUI in my server)

---

### Post by wojox on 2009-09-25
Try it again. I just copied a couple address and it loaded.

---

