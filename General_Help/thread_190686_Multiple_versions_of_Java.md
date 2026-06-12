---
title: "Multiple versions of Java"
date: 2006-06-06
forum: General Help
---

### Post by tad604 on 2006-06-06
I'm kind of a linux newb, but I'm becoming more and more comfortable (especially using kde) but I do have a fair amount of experience programming (specifically in java on a windows environment) and with that in mind, I would like to find out how to install multiple version of java on Ubuntu.

I managed to install Eclipse using the package manager and that installed the 1.4 jdk.  I would really like to get Java 5 installed as the default java but would prefer to keep 1.4 (and possibly install java 6) and be able to switch between the three.  Can anyone point me to a tutorial on how to do this (or walk me through it)?  Bonus points to anyone who can tell me how to install Net Beans too.

---

### Post by sarhento_lobo on 2006-06-13
Depends on how you intend to use the "switching". If you just want to switch the jdk that your IDE is using, it should be done internally, from within the IDE itself (you'll usually have to specify directly the install location of your desired jdk).

---

### Post by 23meg on 2006-06-13
For the JRE you can use```
sudo update-alternatives --config java

```

---

### Post by Hemmer on 2006-08-29
> **23meg said:**
> For the JRE you can use```
sudo update-alternatives --config java

```
cheers i was looking for this to get my azurues working with java. nice one... :D

---

