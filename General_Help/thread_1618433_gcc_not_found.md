---
title: "gcc not found"
date: 2010-11-10
forum: General Help
---

### Post by casualmwg on 2010-11-10
1) Installed Sever Lucid 10.04
 
2) Packages installed successfully:
a) cpp [version 4:4.4.3-1ubuntu1]
b) cpp-4.4 [version 4.4.3-4ubuntu5]
c) gcc-4-4-base [version 4.4.3-4ubuntu5]
 
3) When attempting to execute 'gcc' it is not located
 
4) whereis gcc -- produces a result of gcc: /usr/lib/gcc
 
Question: Not sure what additional steps are required to incorporate the GCC compiler within this enviroment?

---

### Post by oldos2er on 2010-11-10
I think you also need to install **build-essential**

---

### Post by efflandt on 2010-11-10
```
efflandt@XPS-8100:~$ ls -l /usr/bin/*gcc*
-rwxr-xr-x 1 root root    428 2009-06-12 11:05 /usr/bin/c89-gcc
-rwxr-xr-x 1 root root    451 2009-06-12 11:05 /usr/bin/c99-gcc
lrwxrwxrwx 1 root root      7 2010-10-28 00:00 /usr/bin/gcc -> gcc-4.4
-rwxr-xr-x 1 root root 259232 2010-09-27 14:14 /usr/bin/gcc-4.4
lrwxrwxrwx 1 root root      7 2010-10-28 00:00 /usr/bin/x86_64-linux-gnu-gcc -> gcc-4.4
lrwxrwxrwx 1 root root      7 2010-10-28 00:00 /usr/bin/x86_64-linux-gnu-gcc-4.4 -> gcc-4.4
```

See if the symlink exists in /usr/bin (this is Maverick).  I was thinking I had to create that link in 10.04, but maybe that was to symlink g++ to its specific version.

---

### Post by casualmwg on 2010-11-11
Thanks for reply.
 
Quick question.
 
I installed from a CD, but do not currently have an internet connection from the server to execute 'app-get install build-essential'.
 
I attempted pulling the package for a machine with internet connectivity and copying it over and installing it with dpkg, but that lead to other packages required.
 
Eventually stating no valid C compier in the path exists attemting to install dpkg-dev.
 
Am I out of luck here, until I get an internet connection to the server or are there other alternatives I can follow?

---

### Post by oldos2er on 2010-11-11
Build-essential may be on the CD, so try setting the CD as a source. Insert the CD, and run **sudo apt-cdrom add && sudo apt-get update && sudo apt-get install build-essential**

---

### Post by casualmwg on 2010-11-11
Executed the following:
 
1) sudo apt-cdrom add
 
    The command mounted /dev/sr0 on /media/apt type iso9660 (ro)
 
 
2) sudo apt-get install build-essential
 
Receive the following error:
 
Failed to fetch cdrom:[Ubuntu-Server 10.04 1 LTS _Lucid Lynx_ - Release i386 (20100816)]/pool/main/b/buil-essential/build-essential_11.4.1_all.deb  File not found
 
 
That file is on the CD at that location, so I am not sure why it is not found.

---

### Post by casualmwg on 2010-11-12
I connected my server to the internet and resolved my issues.  Thanks for your input.

---

### Post by oldos2er on 2010-11-12
Glad you got it resolved, just FYI, after you add any source or repository you need to run **sudo apt-get update** to enable it.

---

