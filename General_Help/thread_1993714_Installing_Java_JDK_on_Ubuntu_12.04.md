---
title: "Installing Java JDK on Ubuntu 12.04"
date: 2012-06-02
forum: General Help
---

### Post by gmseed on 2012-06-02
Hi

I downloaded the latest 32bit jdk v7u4 from:

[http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u4-downloads-1591156.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u4-downloads-1591156.html)

which is a .rpm file; ie:

jdk-7u4-linux-i586.rpm

I then followed the instructions at:

[http://www.noobslab.com/2012/02/install-rpm-packages-on-ubuntulinux.html](http://www.noobslab.com/2012/02/install-rpm-packages-on-ubuntulinux.html)

for converting the .rpm to a .deb file.

However, with the command:

sudo alien packagename.rpm

I get the error:

"the package cannot be built on this system"

Does anyone know the solution to this problem?

Graham

---

### Post by Cheesemill on 2012-06-02
Install it from the WebUpd8 PPA instaed:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by gmseed on 2012-06-02
Hi

Thanks for your reply. Following your instructions installed the latest jdk fine.

Graham

---

### Post by cthlhu1987 on 2012-08-19
> **Cheesemill said:**
> Install it from the WebUpd8 PPA instaed:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```
:guitar: Thank you very much, java installation without any problems :)

---

