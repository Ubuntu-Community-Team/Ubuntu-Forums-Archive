---
title: "Android Open Source Build Error 41"
date: 2010-01-05
forum: General Help
---

### Post by bluestar14 on 2010-01-05
i tried to build android open source, and got this error(i had already ran make before, thats why so short):
```
avin@STUDYROOML:~$ export ANDROID_JAVA_HOME=$JAVA_HOME 
avin@STUDYROOML:~$ cd mydroid
avin@STUDYROOML:~/mydroid$ make
============================================
PLATFORM_VERSION_CODENAME=AOSP
PLATFORM_VERSION=AOSP
TARGET_PRODUCT=generic
TARGET_BUILD_VARIANT=eng
TARGET_SIMULATOR=
TARGET_BUILD_TYPE=release
TARGET_ARCH=arm
HOST_ARCH=x86
HOST_OS=linux
HOST_BUILD_TYPE=release
BUILD_ID=MASTER
============================================
/bin/bash: line 0: cd: development/tools/layoutopt/app/src/resources: No such file or directory
Install: out/host/linux-x86/framework/apicheck.jar
Install: out/host/linux-x86/framework/clearsilver.jar
Install: out/host/linux-x86/framework/droiddoc.jar
Install: out/host/linux-x86/lib/libneo_util.so
Install: out/host/linux-x86/lib/libneo_cs.so
Install: out/host/linux-x86/lib/libneo_cgi.so
Install: out/host/linux-x86/lib/libclearsilver-jni.so
target Java: core (out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes)
/bin/bash: line 1:  3956 Killed                  javac -J-Xmx512M -target 1.5 -Xmaxerrs 9999999 -encoding ascii -bootclasspath out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes.jar -g -extdirs "" -d out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes \@out/target/common/obj/JAVA_LIBRARIES/core_intermediates//java-source-list-uniq
make: *** [out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes-full-debug.jar] Error 41

```

---

### Post by bodhi.zazen on 2010-01-05
No offense but is there some reason you are not using the android forums

[http://androidforums.com/](http://androidforums.com/)

or android mailing list ?

---

### Post by bluestar14 on 2010-01-05
yes, because, i have tried posting there once, and i never got a reply, on ubuntu forums, replies come quickly, but i will try, not that i still don't hope for an answer here

---

### Post by Trust-No-1 on 2010-07-06
I feel your pain, i get a similar error, posted on official android, dont have a reply, same on here. all my posts are ignored. *Sigh*

---

