---
title: "Any good JAR player/emulator out there?"
date: 2011-08-10
forum: General Help
---

### Post by rva1945 on 2011-08-10
I'd like to install a JAR player in order to test JAR files before installing into my cell (a SonyEricsson w150a, a.k.a. Yizo).

Ubuntu 10.10 Maverick.

Thanks
Robert

---

### Post by WorMzy on 2011-08-10
Uh.. you mean like the Java Runtime Environment that's installed by default?

---

### Post by rva1945 on 2011-08-10
> **WorMzy said:**
> Uh.. you mean like the Java Runtime Environment that's installed by default?
 
 
GREAT! So I already have the tool to run JAR files?

---

### Post by gandaran on 2011-08-10
> **rva1945 said:**
> GREAT! So I already have the tool to run JAR files?
if you haven't installed openjdk-java or sun-java yet then no you haven't, you can install any of them from software center but for sun-java you need to enable the canonical partner repository in software sources and update software package list then you will find all sun-java packages in software center ready for install.

---

### Post by WorMzy on 2011-08-10
My bad, I thought Ubuntu came with it pre-installed.

Install it with the following command
```
sudo apt-get install openjdk-6-jre
```

---

### Post by rva1945 on 2011-08-10
> **gandaran said:**
> if you haven't installed openjdk-java or sun-java yet then no you haven't, you can install any of them from software center but for sun-java you need to enable the canonical partner repository in software sources and update software package list then you will find all sun-java packages in software center ready for install.

The OpenJDK Java 6 Runtime is installed. When I tried to open a JAR file (it runs in my cel), I got a message about mhaving to mark it as executable, did it, now no messages but nothing happens when I right-click on the file and select the Open with OpenJDK Java 6 Runtime option.

All I wish is to run the JAR files in my PC.

Thanks

---

### Post by WorMzy on 2011-08-10
Try running it from a terminal.

```
java -jar /path/to/file.jar
```

It may give you some indication as to why nothing seems to be happening (e.g. an error)

---

### Post by rva1945 on 2011-08-12
> **WorMzy said:**
> Try running it from a terminal.

```
java -jar /path/to/file.jar
```

It may give you some indication as to why nothing seems to be happening (e.g. an error)

Done, and the output is:


Failed to load Main-Class manifest attribute from (jar file).

---

