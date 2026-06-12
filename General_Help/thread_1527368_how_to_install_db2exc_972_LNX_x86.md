---
title: "how to install db2exc_972_LNX_x86"
date: 2010-07-09
forum: General Help
---

### Post by safyras on 2010-07-09
Hello i am using ubuntu 10.04 then i extract  db2exc_972_LNX_x86.tar.gz and then i am trying to install this i am getting error 

[HTML]ERROR: 
   The required library file libaio.so.1 is not found on the system. 
   Check the following web site for the up-to-date system requirements
   of IBM DB2 9.7
   http://www.ibm.com/software/data/db2/udb/sysreqs.html
   http://www.software.ibm.com/data/db2/linux/validate  
  Aborting the current installation ...
  Run installation with the option "-f sysreq" parameter to force the installation.
[/HTML]

---

### Post by ThomasDenmark on 2010-08-23
I do also have this problem, and would like an answer, if anybody has one.

---

### Post by ThomasDenmark on 2010-08-23
Ok, I found it. 

libaio.so.1 seems to be a file needed by most database systems. 

One way of installing the file is using APT:

```
sudo apt-get install libaio1
```

---

