---
title: "installing wavsplit in 64 machine"
date: 2011-09-15
forum: General Help
---

### Post by sn0m on 2011-09-15
Hi
Does anybody know how to install a 32bit application on a 64bit machine.
I have natty 64 bit on my laptop but would like to use wavsplit that is a 32bit application.
This is what I have done:
koli@koli-K53E:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
koli@koli-K53E:~$ 
ok now tried to install package:
koli@koli-K53E:~$ sudo dpkg -i /home/koli/Documents/linux/programs/wavsplit_1.1.0-3_i386.deb 
dpkg: error processing /home/koli/Documents/linux/programs/wavsplit_1.1.0-3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 /home/koli/Documents/linux/programs/wavsplit_1.1.0-3_i386.deb
koli@koli-K53E:~$ 

Is there a way to install this?
thanks
sokol

---

### Post by dcstar on 2011-09-17
> **sn0m said:**
> Hi
Does anybody know how to install a 32bit application on a 64bit machine.
I have natty 64 bit on my laptop but would like to use wavsplit that is a 32bit application.
.........

Or you could simply install a native 64-bit app that does the same job: **wavbreaker**

---

### Post by oldos2er on 2011-09-17
> **sn0m said:**
> 
koli@koli-K53E:~$ sudo dpkg -i /home/koli/Documents/linux/programs/wavsplit_1.1.0-3_i386.deb 
dpkg: error processing /home/koli/Documents/linux/programs/wavsplit_1.1.0-3_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 /home/koli/Documents/linux/programs/wavsplit_1.1.0-3_i386.deb
koli@koli-K53E:~$ 

Is there a way to install this?
thanks
sokol

**sudo dpkg -i --force-architecture /home/koli/Documents/linux/programs/wavsplit_1.1.0-3_i386.deb**

**man dpkg** for more info.

---

### Post by sn0m on 2011-09-18
Thanks mate, wavsplit works fine now.
I had to use wavsplit as it works from command line in automated scripts.

---

