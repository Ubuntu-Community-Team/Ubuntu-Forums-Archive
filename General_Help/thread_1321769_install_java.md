---
title: "install java"
date: 2009-11-10
forum: General Help
---

### Post by micio8 on 2009-11-10
Since I have installed ubuntu 9.10 i'm having this problem installing java:

fabio@ubuntu01:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
fabio@ubuntu01:~$ 

????

---

### Post by alphaniner on 2009-11-10
What java packages do you have installed?

```
aptitude search sun-java6 |grep ^i
```

Edit:

> sun-java6-plugin: Depends: sun-java6-bin (= **6-15-1**) but **6-16-0ubuntu1.9.04** is to be installed

6-15-1 is the version for Karmic.  6-16-0ubuntu1.9.04 is the version for Jaunty.  Maybe your sources got messed up somehow?  Did you upgrade?

---

### Post by micio8 on 2009-11-10
> **alphaniner said:**
> What java packages do you have installed?

```
aptitude search sun-java6 |grep ^i
```Edit:



6-15-1 is the version for Karmic.  6-16-0ubuntu1.9.04 is the version for Jaunty.  Maybe your sources got messed up somehow?  Did you upgrade?

Thanks for your reply......Problem solved now.....i needed to disinstall java then reinstall again.....i think there were bin file corrupted from previous ubuntu version:p

---

