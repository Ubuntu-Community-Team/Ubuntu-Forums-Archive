---
title: "Apt-get problem"
date: 2011-03-25
forum: General Help
---

### Post by siddhantchd on 2011-03-25
i m having a problem when i try to get the package using the apt-get command

> sid@Sid-Laptop:~$ sudo apt-get install minicom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package minicom


please help guys......

---

### Post by WorMzy on 2011-03-25
That package is in the Universe repo, [check your software sources]("https://help.ubuntu.com/community/Repositories/Ubuntu#Missing%20repositories%20in%20Ubuntu%2010.10") and make sure that you have this repo enabled.

If it is, then make sure that your package information is up-to-date by running
```
sudo apt-get update
```

---

### Post by nothingspecial on 2011-03-25
Go system > administration > synaptic package manager and enable the universe repository then click reload.

---

### Post by rexbelia on 2011-09-17
I tried doing what you said, it says "The repository may no longer be available or could not be contacted because of network problems..."

How do I get my internet working in Ubuntu? I'm using it virtually via VMware.

Thanks.

---

