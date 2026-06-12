---
title: "Eclipse Galileo... where is java???"
date: 2009-11-14
forum: General Help
---

### Post by heepie on 2009-11-14
I can't seem to make a java project from eclipse... I installed Galileo but doesn't seem to find java.

I know i have java installed:

&java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)

&javac -version
javac 1.6.0_15

If I go to in eclipse window>preferences I can't find java anywhere...

I'm sure is a very silly thing... I'm studying java in college where we use textpad from windows but i would like to get familiar with eclipse in Linux...

---

### Post by heepie on 2009-11-14
i tried 

&sudo update-alternatives --config java

and changing to java-6-sun but it didn't resolve the problem

the output of &java -version now is:

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

I restart eclipse window>preferences ... no java

help !!!

---

### Post by heepie on 2009-11-14
installing eclipse-jdt from synaptic solved the problem

---

