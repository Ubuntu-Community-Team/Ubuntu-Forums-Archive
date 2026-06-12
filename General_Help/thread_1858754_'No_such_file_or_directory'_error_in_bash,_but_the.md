---
title: "'No such file or directory' error in bash, but the file exists?"
date: 2011-10-13
forum: General Help
---

### Post by mjsilverstri on 2011-10-13
On Ubuntu 11.10, I get a 'No such file or directory' error when I try to execute a command (adb command in android sdk).

I have checked with 'ls -la' , the file 'adb' is there and it has 'x' flag So why I am getting a 'No such file or directory'?

> ~/Programs/android-sdk-linux_x86/platform-tools$ ./adb
 bash: ./adb: No such file or directory
~/Programs/android-sdk-linux_x86/platform-tools$ ls -la
 total 34120
 drwxrwxr-x 3 silverstri silverstri     4096 2011-10-08 18:50 .
 drwxrwxr-x 8 silverstri silverstri     4096 2011-10-08 18:51 ..
 -rwxrwxr-x 1 silverstri silverstri  3764858 2011-10-08 18:50 aapt
 -rwxrwxr-x 1 silverstri silverstri   366661 2011-10-08 18:50 adb
 -rwxrwxr-x 1 silverstri silverstri   906346 2011-10-08 18:50 aidl
 -rwxrwxr-x 1 silverstri silverstri   328445 2011-10-08 18:50 dexdump
 -rwxrwxr-x 1 silverstri silverstri     2603 2011-10-08 18:50 dx
 drwxrwxr-x 2 silverstri silverstri     4096 2011-10-08 18:50 lib
 -rwxrwxr-x 1 silverstri silverstri 14269620 2011-10-08 18:50 llvm-rs-cc
 -rwxrwxr-x 1 silverstri silverstri 14929076 2011-10-08 18:50 llvm-rs-cc-2
 -rw-rw-r-- 1 silverstri silverstri      241 2011-10-08 18:50 llvm-rs-cc.txt
 -rw-rw-r-- 1 silverstri silverstri   332494 2011-10-08 18:50 NOTICE.txt
 -rw-rw-r-- 1 silverstri silverstri      291 2011-10-08 18:50 source.properties

---

### Post by Vaphell on 2011-10-13
maybe 32bit vs 64bit issue?
```
uname -m
file adb
```

---

### Post by dcstar on 2011-10-13
> **Vaphell said:**
> maybe 32bit vs 64bit issue?

+1

Install the **ia32-libs** package.

---

### Post by sublimeowl on 2011-10-20
I have the ia32-libs installed but still get the "no such file" error

---

### Post by 2F4U on 2011-10-20
What happens if you execute it as 

**. ./adb**

Please note the additional ".".

---

### Post by eyelessfade on 2011-10-25
I think this is the [problem]("http://www.ubuntugeek.com/new-features-in-ubuntu-11-10-oneiric.html")! ia32-lib is not what it was

---

### Post by oldos2er on 2011-10-25
Maybe this bug is affecting you: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

---

### Post by eyelessfade on 2011-10-26
> **oldos2er said:**
> Maybe this bug is affecting you: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

Thanks that worked great.

---

