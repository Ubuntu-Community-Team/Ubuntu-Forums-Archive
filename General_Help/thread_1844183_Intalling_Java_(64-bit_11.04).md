---
title: "Intalling Java (64-bit 11.04)"
date: 2011-09-14
forum: General Help
---

### Post by elisimmer on 2011-09-14
I'm having issues installing 64 bit Java on Ubuntu 11.04.
Normally I would just install the OpenJDK from the software center, but I want to be certain I'm getting the 64-bit version.

Yes this is about Minecraft performance.

Any help or a link to GOOD instructions would be appreciated.

---

### Post by SavageWolf on 2011-09-14
I just checked my version of the OpenJDK, it's 64 bit, so it should be in the Software Centre.

---

### Post by elisimmer on 2011-09-14
I've now installed OpenJDK, how do I check for myself?

---

### Post by SavageWolf on 2011-09-15
Open up a terminal and type: ```

java -version
```

---

### Post by 3rdalbum on 2011-09-15
> **elisimmer said:**
> I'm having issues installing 64 bit Java on Ubuntu 11.04.
Normally I would just install the OpenJDK from the software center, but I want to be certain I'm getting the 64-bit version.

Yes this is about Minecraft performance.

Any help or a link to GOOD instructions would be appreciated.

If it's in Software Center on 64-bit Ubuntu, then it's a 64-bit program. The only exception is when the program simply doesn't work when compiled for 64-bit; in which case, Software Center contains only the 32-bit version, because there are no 64-bit versions available.

---

### Post by Governa on 2011-09-15
Newbie question here, are there two JAVA VM options in Ubuntu, OpenJDK and Sun's? I ask this because I have seen in more than one place devs suggesting to "please use Sun's JVM." I'm assuming then that we can opt for an opensource implementation such as OpenJDK and a more proprietary one such as Sun's?

If so:

1- I'm I correct to assume that Sun's provides in general better performance for Java apps, that's why devs recommend it?

2- If that's the case, how can I install Sun's Java SE 7 or SE 6 update 27? Should I opt for the RPM installer or compressed binary? How do you do it?

3- Is there any repository for Sun's Java VM so that I can easialy upgrade when a new version is out? I seem to be running an older version (update 22 or equivalent)

4- I am running 11.04 64bit and the following Java VM:

java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

If I install Sun's JVM should I uninstall OpenJDK first? Should I install Sun's 64bit JVM + 32bit JVM or it's unnecessary?

---

