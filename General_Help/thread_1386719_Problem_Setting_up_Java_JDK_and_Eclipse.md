---
title: "Problem Setting up Java JDK and Eclipse"
date: 2010-01-21
forum: General Help
---

### Post by n125 on 2010-01-21
Hi, I might be overlooking something obvious, but I can't seem to get Eclipse to detect the Java JDK that I installed through Synaptic Package Manager (sun-java6-jdk):

> :~$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)I obtained Eclipse IDE from the Ubuntu Software Centre, and it looks like this:

[[IMG]http://img193.imageshack.us/img193/4985/screenshotjavaeclipsesd.th.png[/IMG]]("http://img193.imageshack.us/i/screenshotjavaeclipsesd.png/")

As I understand it, there should be a Java submenu in Windows >> Preferences that lets me set the Java version for Eclipse to use, but in my case, the submenu isn't there at all.

Any tips? Thanks.

---

### Post by AlexZaim on 2010-01-21
Not sure how to help you on this, but.. i did the following way:
Downloaded Eclispe from the official site
Downloaded jdk from the official site (or was it jre?)
un-packed it ,renamed it to "jdk"/ "jre" and just pasted it in the Eclipse folder.

After that eclipse works perfectly.

---

### Post by n125 on 2010-01-21
> **AlexZaim said:**
> Not sure how to help you on this, but.. i did the following way:
Downloaded Eclispe from the official site
Downloaded jdk from the official site (or was it jre?)
un-packed it ,renamed it to "jdk"/ "jre" and just pasted it in the Eclipse folder.

After that eclipse works perfectly.

Thanks for the reply!

This might be silly, but how do I unpack it, and where is the Eclipse folder? It comes as *jdk-6u18-linux-i586.bin*, and Ubuntu says it's an unknown file-type when I double click it. I'm still pretty new to Linux, so I'm still pretty clueless when it comes to doing some things.

---

### Post by Queue29 on 2010-01-22
```
sudo apt-get install eclipse-jdt
```

will install the java plugins (without the download and unzip method)

---

### Post by n125 on 2010-01-22
> **Queue29 said:**
> ```
sudo apt-get install eclipse-jdt
```will install the java plugins (without the download and unzip method)

 This did the trick. Thanks!

---

