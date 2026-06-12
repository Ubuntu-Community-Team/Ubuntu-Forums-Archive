---
title: "Binary throwing strange bash error."
date: 2010-09-10
forum: General Help
---

### Post by Eyes Only on 2010-09-10
Hello everyone, I apologize if this is the wrong section but i didnt notice an "Advanced Support" section here. I am currently trying to get Google's Android Debug Bridge working, which is as simple as running one of the executables in the sdk's tools folder. It seems to be blatantly refusing to run the binary. Here is the command and more info on the actual file:
```

jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ file adb
adb: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, not stripped
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ ls
adb      ant         ddms         draw9patch  etc1tool         hprof-conv  lib       NOTICE.txt         sqlite3    zipalign
android  apkbuilder  dmtracedump  emulator    hierarchyviewer  layoutopt   mksdcard  source.properties  traceview
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ ./adb
bash: ./adb: No such file or directory
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ ls -la
total 9604
drwxrwxr-x 4 jonhaller jonhaller    4096 2010-08-28 20:43 .
drwxrwxr-x 5 jonhaller jonhaller    4096 2010-08-30 15:24 ..
-rwxrwxrwx 1 jonhaller jonhaller  339885 2010-08-28 20:43 adb
-rwxrwxrwx 1 jonhaller jonhaller    3540 2010-08-28 20:43 android
drwxrwxr-x 2 jonhaller jonhaller    4096 2010-08-28 20:43 ant
-rwxrwxrwx 1 jonhaller jonhaller    1977 2010-08-28 20:43 apkbuilder
-rwxrwxrwx 1 jonhaller jonhaller    3265 2010-08-28 20:43 ddms
-rwxrwxrwx 1 jonhaller jonhaller   89016 2010-08-28 20:43 dmtracedump
-rwxrwxrwx 1 jonhaller jonhaller    1940 2010-08-28 20:43 draw9patch
-rwxrwxrwx 1 jonhaller jonhaller 6988224 2010-08-28 20:43 emulator
-rwxrwxrwx 1 jonhaller jonhaller  480634 2010-08-28 20:43 etc1tool
-rwxrwxrwx 1 jonhaller jonhaller    1987 2010-08-28 20:43 hierarchyviewer
-rwxrwxrwx 1 jonhaller jonhaller   23068 2010-08-28 20:43 hprof-conv
-rwxrwxrwx 1 jonhaller jonhaller    1939 2010-08-28 20:43 layoutopt
drwxrwxr-x 4 jonhaller jonhaller    4096 2010-08-28 20:43 lib
-rwxrwxrwx 1 jonhaller jonhaller   16574 2010-08-28 20:43 mksdcard
-rw-rw-r-- 1 jonhaller jonhaller  195080 2010-08-28 20:43 NOTICE.txt
-rw-rw-rw- 1 jonhaller jonhaller      33 2010-08-28 20:43 source.properties
-rwxrwxrwx 1 jonhaller jonhaller 1447960 2010-08-28 20:43 sqlite3
-rwxrwxrwx 1 jonhaller jonhaller    3044 2010-08-28 20:43 traceview
-rwxrwxrwx 1 jonhaller jonhaller  188373 2010-08-28 20:43 zipalign
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ file adb
adb: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, not stripped
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ sudo ./adb
[sudo] password for jonhaller: 
sudo: unable to execute ./adb: No such file or directory
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ 

```

in other words: me: "./adb" bash: "NO U!". also maverick 64bit RC

---

### Post by ubulal on 2010-09-10
Really strange and misleading error message.  Do you have the 32 bit compatibility libs installed? (if there is such a thing in maverick, I'm no expert here)  Try "ldd adb" to look for missing library dependencies.

---

### Post by Eyes Only on 2010-09-10
```
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ ldd ./adb
    not a dynamic executable
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ ldd adb
    not a dynamic executable
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ ldd "~/Downloads/android-sdk-linux_x86/tools/adb"
ldd: ~/Downloads/android-sdk-linux_x86/tools/adb: No such file or directory
jonhaller@jonhaller-laptop:~/Downloads/android-sdk-linux_x86/tools$ 

```lol i think maverick officially hates me

---

### Post by ubulal on 2010-09-10
Looks like some unhandled case and hence generic error message somewhere in the part of system responsible for starting programs.  Is there a package ia32-libs on maverick?

---

### Post by Eyes Only on 2010-09-10
Thats what i thought it was. and installing ia32-libs solved the problem (why would maverick come with it not installed?) damn, you are very impressive. the people at the irc channel had no clue... your assistance is greatly appreciated man, keep up the good work ;)

a gold star for you! :KS  cheers! -jon

---

### Post by ubulal on 2010-09-10
Thanks :)

---

### Post by skitzandroid on 2011-03-06
> **ubulal said:**
> Looks like some unhandled case and hence generic error message somewhere in the part of system responsible for starting programs.  Is there a package ia32-libs on maverick?

Thanks!  problem solved for me too!

---

