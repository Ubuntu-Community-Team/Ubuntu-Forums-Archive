---
title: "Java crash: Assertion `obj-&gt;Pointer' failed."
date: 2011-07-25
forum: General Help
---

### Post by n2o-Gr55 on 2011-07-25
So, every so often while playing Minecraft (Yes, yes, a game) Java would just close every so often.

I never got to see an error message, as I was running it with a shell script from a launcher

Anyway, so after a bit of playing (Haven't found a way to reproduce it, happens at seemingly random times) The java window closes, leaving this in the terminal:

```
java: intel_buffer_objects.c:466: intel_bufferobj_unmap: Assertion `obj->Pointer' failed.
/home/usr/Minecraft.sh: line 1:  4771 Aborted                 java -Xmx1024M -Xms512M -cp '/home/me/minecraft.jar' net.minecraft.LauncherFrame
```Minecraft.sh contains
 ```
java -Xmx1024M -Xms512M -cp '/home/me/minecraft.jar' net.minecraft.LauncherFrame

```java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)

Thanks for your help in advance.

---

### Post by n2o-Gr55 on 2011-07-26
Shameful bump.

---

### Post by Azdour on 2011-07-26
Hi,

Never played Minecraft but you may want to try the Oracle/Sun JDK to see if its more stable.

---

### Post by Gyokuro on 2011-07-26
You should use sun-java6u26

---

### Post by Gremlinzzz on 2011-07-26
> **n2o-Gr55 said:**
> So, every so often while playing Minecraft (Yes, yes, a game) Java would just close every so often.

I never got to see an error message, as I was running it with a shell script from a launcher

Anyway, so after a bit of playing (Haven't found a way to reproduce it, happens at seemingly random times) The java window closes, leaving this in the terminal:

```
java: intel_buffer_objects.c:466: intel_bufferobj_unmap: Assertion `obj->Pointer' failed.
/home/usr/Minecraft.sh: line 1:  4771 Aborted                 java -Xmx1024M -Xms512M -cp '/home/me/minecraft.jar' net.minecraft.LauncherFrame
```Minecraft.sh contains
 ```
java -Xmx1024M -Xms512M -cp '/home/me/minecraft.jar' net.minecraft.LauncherFrame

```java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)

Thanks for your help in advance.

you might want to uninstall icetea and try

sudo apt-get install sun-java6-jre sun-java6-plugin

---

