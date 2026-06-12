---
title: "No such file or directory"
date: 2010-11-06
forum: General Help
---

### Post by naveenyes on 2010-11-06
I recently updated from **lucid to maverick**. I was running Helix Media server on my lucid. After update when I tried to run the server I got the below mentioned error. 
**bash: /.mbrs1400-ga-linux-rhel5.bin: No such file or directory**

I also **removed the KDE desktop** and a lots of unused applications after update. So not sure if its because of the update.

I tried to reinstall the Helix server and I am getting the same error when i try to execute the executable file. 

**bash: /.mbrs1400-ga-linux-rhel5.bin: No such file or directory**

I was executing the same file before upgrade. I have rights to execute the files. 

ls -l displays the file.
-rwxrwxrwx 1 navis navis 34282276 mbrs1400-ga-linux-rhel5.bin
-rwxrwxrwx 1 navis navis 34171327 mbrs1400-ga-linux-rhel5.tar.gz

I came across a similar issue in some forum and found that installation **ia32-libs** solved this issue. But I am not able to install ia32-libs. Its not available in the Synaptic Package manager. In need of help. Thanks in Advance.

---

### Post by oldos2er on 2010-11-06
ia32-libs is in the universe repository; make sure you have it enabled, then run **sudo apt-get update**.

---

### Post by dcstar on 2010-11-07
> **naveenyes said:**
> I recently updated from **lucid to maverick**. I was running Helix Media server on my lucid. After update when I tried to run the server I got the below mentioned error. 
**bash: /.mbrs1400-ga-linux-rhel5.bin: No such file or directory**

I also **removed the KDE desktop** and a lots of unused applications after update. So not sure if its because of the update.

I tried to reinstall the Helix server and I am getting the same error when i try to execute the executable file. 

**bash: /.mbrs1400-ga-linux-rhel5.bin: No such file or directory**

I was executing the same file before upgrade. I have rights to execute the files. 

ls -l displays the file.
-rwxrwxrwx 1 navis navis 34282276 mbrs1400-ga-linux-rhel5.bin
-rwxrwxrwx 1 navis navis 34171327 mbrs1400-ga-linux-rhel5.tar.gz

I came across a similar issue in some forum and found that installation **ia32-libs** solved this issue. But I am not able to install ia32-libs. Its not available in the Synaptic Package manager. In need of help. Thanks in Advance.

Packages compiled for 32-bit platforms will not run on 64-bit systems.

---

### Post by naveenyes on 2010-11-07
**@oldos2er** - universe repository is enabled. Still I am not able to find ia32-libs.
**@dcstar** - I run 32 bit Ubuntu. 
uname -a
Linux <hostName> 2.6.35-23-generic #36-Ubuntu SMP Tue Oct 26 17:03:18 UTC 2010 **i686** GNU/Linux

And the application was working before i updated to maverick, removed KDE desktop completely and removed a lots of unused applications.
As I run the 32 bit version, I believe i should not need the ia32-libs. Waiting for help. Thanks.

---

### Post by oldos2er on 2010-11-07
ia32-libs: Description: ia32 shared libraries for use on amd64 and ia64 systems
 This package contains runtime libraries for the ia32/i386
 architecture, configured for use on an amd64 or ia64 Debian system running
 a 64-bit kernel.

So that's probably why it's not in the 32-bit repos. Try [http://packages.ubuntu.com/search?keywords=ia32-libs+&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=ia32-libs+&searchon=names&suite=maverick&section=all)

---

### Post by mason_ on 2010-11-23
I got the same problem today.
Same error message showed up when I was executing mbrs1401-ga-linux-rhel5.bin in Ubuntu 10.04.
It was my first time installing Helix. And I did not remove any application.

---

