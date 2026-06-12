---
title: "Android Open Source On Karmic Koala"
date: 2009-12-16
forum: General Help
---

### Post by bluestar14 on 2009-12-16
I am trying to install the android open source onto 9.10, but when i try to build it, it says:
```
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
/bin/bash: line 1: 11527 Killed                  javac -J-Xmx512M -target 1.5 -Xmaxerrs 9999999 -encoding ascii -bootclasspath out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes.jar -g -extdirs "" -d out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes \@out/target/common/obj/JAVA_LIBRARIES/core_intermediates//java-source-list-uniq
make: *** [out/target/common/obj/JAVA_LIBRARIES/core_intermediates/classes-full-debug.jar] Error 41

```

---

### Post by bluestar14 on 2009-12-16
i did try the troubleshooter on website

---

### Post by bluestar14 on 2009-12-16
this is really urgent

---

