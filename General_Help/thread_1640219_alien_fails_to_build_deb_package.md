---
title: "alien fails to build deb package"
date: 2010-12-07
forum: General Help
---

### Post by cthlhu1987 on 2010-12-07
I downloaded the newest java jdk installation archive (rpm in a executable shel archive), extracted them with 7z and tried to convert them to deb packages via alien, but it wouldn't do that, only gave me the following error message:
```
Package build failed; could not run generated debian/rules file.
```
I tried it with and without "--scripts"-argument, but to no avail. Could anyone help me, please?

---

### Post by chenxiaolong on 2011-01-10
Make sure that the rpm is on a Linux-based partition, like ext4. If it's on an NTFS partition (Windows-based). NTFS partitions can't store the executable file permission that scripts require in order to run (this is a security feature of Linux). If the rpm is stored on an NTFS partition, just move it to your desktop, for example, and run Alien again.

If all you want to do is install the Java JDK, you can install it from the Ubuntu repositories:

1) **Open source OpenJDK:**

```
sudo apt-get install openjdk-6-jdk
```

2) **Sun/Oracle JDK ([www.java.com](www.java.com) version):**

```
gksudo gedit /etc/apt/sources.list
```

Find this section: 

> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

and remove the '#' from the last two lines of that section so that it reads:

> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

Then, run:

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

You will get automatic updates by installing from the repositories.

Sorry for the long post. I hope this works out for you!

---

