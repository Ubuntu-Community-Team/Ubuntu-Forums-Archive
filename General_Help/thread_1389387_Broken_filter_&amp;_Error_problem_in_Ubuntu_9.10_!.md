---
title: "Broken filter &amp; Error problem in Ubuntu 9.10 !"
date: 2010-01-24
forum: General Help
---

### Post by Nirob on 2010-01-24
Hello,

I'm facing a problem updating My Ubuntu OS, it says there is 4 broken filter (Error:broken count), I'm trying to reinstall those but i cant. there is another error on update that was following error: 

E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb: subprocess new pre-removal script returned error exit status 2

How can i solve this problem.

Thank you.

---

### Post by Soul-Sing on 2010-01-25
```
gksudo nautilus
```
navigate to /var/lib/dpkg/info and deleting everything that has this name:
- bandwidthd_2.0.1
remove it
close nautilus
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by AllanP on 2010-02-01
Remove

---

