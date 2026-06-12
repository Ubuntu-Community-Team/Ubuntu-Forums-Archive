---
title: "Problem with JRE and glibc2.2"
date: 2006-01-23
forum: General Help
---

### Post by datavortex on 2006-01-23
Hello,

 I am an old RedHat user, but relatively new to Ubuntu.

 Today I am trying to get Java working, however I am having some issues.  I am hoping someone has run into these before and can shed some light on the matter.

I installed Sun's JRE 1.5.0_06 using the [instructions](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca) from the Wiki guide.  This seems to have worked just fine:
> 
root@lfine:/usr/lib# java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)


However my java apps (from Oracle) still are unhappy, not liking the standard libc++ that cmoes with breezy:
> 
/tmp/install.dir.29630/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory


I found a very helpful [reference](http://www.scoopal.com/node/25) to this problem and tried to remedy it following the instructions on that page.  However, the version of the downward compatible libstdc++ referenced in the article (libstdc++-3-libc6.2-2-2.10.0 from package "libstdc++2.9-glibc2.1") is no longer in any repository I can find.  It appears to have been deprecated and replaced with the downcompat package "libstdc++2.10-glibc2.2".  Unfortunately, if I try to symlink this new library to the old glibc2.1 name like so:
> 
root@lfine:/usr/lib# ln -s libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2


I get a segfault from my java application:
> 
Error occurred during initialization of VM
Unable to load native library: /tmp/install.dir.30063/Linux/resource/jre/lib/i386/libjava.so: symbol __libc_wait, version GLIBC_2.0 not defined in file libc.so.6 with link time reference


Does anyone know if there are any true gcc 2.1 downcompat c++ libs for the current version of Ubuntu?  Know of any other ways to solve this problem?

Thanks much!

---

