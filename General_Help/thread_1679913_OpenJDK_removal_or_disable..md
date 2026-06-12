---
title: "OpenJDK removal or disable."
date: 2011-02-01
forum: General Help
---

### Post by tam2tam on 2011-02-01
OpenJDK has recently updated. Problem is that I am using the JDK from Sun/Oracle which I downloaded and installed along with other java tools and IDE's. I notice that openJDK is now the default JDK on the system. 

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.4) (6b20-1.9.4-0ubuntu1~10.04.1)
OpenJDK Server VM (build 19.0-b09, mixed mode)

Now my own java build is configured in $PATH but ignored, this is not good as I do a lot of java development. I would like to disable the OpenJDK or even remove it. I would also like to disable the update manager for this particular package and it's other add ons.

Any ideas?:popcorn:

---

### Post by tredegar on 2011-02-01
Please try:
```
update-alternatives --config java
```
I just use **jre** not **jdk**, but it'll probably work for you.

---

### Post by tam2tam on 2011-02-02
I used the Ubuntu software centre to remove OpenJDK and it's dependancies and all is well again. I will just wait and see if the update center attempts to update them again.

---

### Post by majeedk1981 on 2012-02-27
> **tam2tam said:**
> I used the Ubuntu software centre to remove OpenJDK and it's dependancies and all is well again. I will just wait and see if the update center attempts to update them again.

How did you un-install the dependencies for open-JDK?

Even after un-installing open-jdk from software center I am still getting updates for 

[LIST=1]
[*]Alternative JVM for OpenJDK using cacao
[*]Alternative JVM for OpenJDK using JamVM
[*]OpenJDK Java Runtime, using Hotspot JIT (headless)
[*]OpenJDK Java runtime (architecture independent libraries)
[/LIST]

---

