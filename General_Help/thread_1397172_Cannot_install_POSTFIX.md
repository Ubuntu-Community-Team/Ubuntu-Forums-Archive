---
title: "Cannot install POSTFIX"
date: 2010-02-02
forum: General Help
---

### Post by karthick87 on 2010-02-02
I am unable to install postfix,i receive the following error.How to fix it?

karthick@Learners-desktop:~$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 1219kB of archives.
After this operation, 3006kB of additional disk space will be used.
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main postfix 2.5.5-1.1
  403 Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.5.5-1.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.5.5-1.1_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by t4thfavor on 2010-02-03
It will be slower for you, but if you change in. to us. in your repos it should work. Looks like that repo is broken.


NM, yours appear to be working now from here.

---

### Post by karthick87 on 2010-02-03
How to fix it?

---

### Post by karthick87 on 2010-02-10
I have changed my repositories to US server and now my problem is fixed...Thanks buddy..

---

