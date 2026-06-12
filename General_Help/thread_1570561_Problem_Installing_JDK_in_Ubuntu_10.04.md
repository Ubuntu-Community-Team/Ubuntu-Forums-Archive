---
title: "Problem Installing JDK in Ubuntu 10.04"
date: 2010-09-08
forum: General Help
---

### Post by j33h4d on 2010-09-08
Hey guys,

Currently, I've Ubuntu 10.04 running in my computer. Before this, I installed OpenJDK in my computer~ This has been prompted when I want to run Dr.Java.

> DrJava cannot find the Java SDK's 'tools.jar' file. This file is necessary to compile files and use the debugger. It is generally located in the 'lib' subdirectory of your Java installation directory. Would you like to specify its location? (If you say 'No', DrJava might be unable to compile or debug programs.)

I choose the file it asked me to choose and this prompted next...

> The file you choose did not appear to be a valid 'tools.jar'. (Your choice might be an incompatible version of the file.) Would you like to pick again? The 'tools.jar' file is generally located in the 'ib' subdirectory under your JDK installation directory. (If you say 'No', DrJava might be unable to compile or debug programs.)

First, I thought there might be a problem with my JDK since that was the first time i used OpenJDK. So, I removed it from my PC and install another JDK+JRE from Synaptic. However, the same thing still happen~

Can you please what is the actual problem? Is the problem cause by my JDK or my Dr.Java? Somehow, I can't remove my Dr.Java since I'm used to it compare to other IDEs. :sad:

ps: I'm using Ubuntu 10.04~ Fresh install~

---

### Post by gandaran on 2010-09-08
have you tried sun-java6-jdk instead or does Dr.Java only work with openjdk-java?

---

### Post by j33h4d on 2010-09-08
Hello gandaran,

thanks for helping me~ any way, problem solved. the problem was actually with Dr.Java itself. I've downloaded the current stable released and it works. :D

> **gandaran said:**
> have you tried sun-java6-jdk instead or does Dr.Java only work with openjdk-java?

---

