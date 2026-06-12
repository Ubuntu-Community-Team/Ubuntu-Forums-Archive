---
title: "Mouse Problem"
date: 2011-05-23
forum: General Help
---

### Post by alexis44 on 2011-05-23
Is there a mouse issue or bug that I need to fix here?  It's a major mouse problem that happens.  When I click on anything, it takes forever and I have to click several times!  Help if you can! :)

---

### Post by linuxinstalledfromhdd on 2011-05-23
Run this command in your terminal and post the results:

[FONT=monospace]** hwinfo --short**[/FONT]

---

### Post by alexis44 on 2011-05-23
jennifer@jennifer-T3616:~$ 
jennifer@jennifer-T3616:~$ hwinfo --short
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
jennifer@jennifer-T3616:~$ sudo apt-get install  hwinfo 
[sudo] password for jennifer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libmono-zeroconf1.0-cil libgdata1.4-cil libgkeyfile1.0-cil libsqlite0
  libmono-messaging2.0-cil libmono-system-messaging2.0-cil libtaglib2.0-cil
  libmono-sqlite2.0-cil libmono-system-web2.0-cil libgudev1.0-cil
  libmono-wcf3.0-cil libgdiplus libnotify0.4-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libhd16
The following NEW packages will be installed:
  hwinfo libhd16
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 744kB of archives.
After this operation, 2,060kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe libhd16 i386 16.0-2 [698kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe hwinfo i386 16.0-2 [46.1kB]                                                                        
Fetched 744kB in 6s (107kB/s)                                                                                                                                
Selecting previously deselected package libhd16.
(Reading database ... 177315 files and directories currently installed.)
Unpacking libhd16 (from .../libhd16_16.0-2_i386.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2_i386.deb) ...
Processing triggers for man-db ...
Setting up libhd16 (16.0-2) ...
Setting up hwinfo (16.0-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jennifer@jennifer-T3616:~$

---

### Post by linuxinstalledfromhdd on 2011-05-23
Okay, run it again for me ..  :P

hwinfo --short

---

### Post by alexis44 on 2011-05-23
jennifer@jennifer-T3616:~$ jennifer@jennifer-T3616:~$ 
jennifer@jennifer-T3616:~$: command not found
jennifer@jennifer-T3616:~$ jennifer@jennifer-T3616:~$ hwinfo --short
jennifer@jennifer-T3616:~$: command not found
jennifer@jennifer-T3616:~$ The program 'hwinfo' is currently not installed.  You can install it by typing:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
jennifer@jennifer-T3616:~$ sudo apt-get install hwinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hwinfo is already the newest version.
The following packages were automatically installed and are no longer required:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libmono-zeroconf1.0-cil libgdata1.4-cil libgkeyfile1.0-cil libsqlite0
  libmono-messaging2.0-cil libmono-system-messaging2.0-cil libtaglib2.0-cil
  libmono-sqlite2.0-cil libmono-system-web2.0-cil libgudev1.0-cil
  libmono-wcf3.0-cil libgdiplus libnotify0.4-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jennifer@jennifer-T3616:~$ jennifer@jennifer-T3616:~$ sudo apt-get install  hwinfo 
jennifer@jennifer-T3616:~$: command not found
jennifer@jennifer-T3616:~$ [sudo] password for jennifer: 
[sudo]: command not found
jennifer@jennifer-T3616:~$ Reading package lists... Done
Reading: command not found
jennifer@jennifer-T3616:~$ Building dependency tree       
Building: command not found
jennifer@jennifer-T3616:~$ Reading state information... Done
Reading: command not found
jennifer@jennifer-T3616:~$ The following packages were automatically installed and are no longer required:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
jennifer@jennifer-T3616:~$   libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
libmono2.0-cil: command not found
jennifer@jennifer-T3616:~$   libmono-zeroconf1.0-cil libgdata1.4-cil libgkeyfile1.0-cil libsqlite0
libmono-zeroconf1.0-cil: command not found
jennifer@jennifer-T3616:~$   libmono-messaging2.0-cil libmono-system-messaging2.0-cil libtaglib2.0-cil
libmono-messaging2.0-cil: command not found
jennifer@jennifer-T3616:~$   libmono-sqlite2.0-cil libmono-system-web2.0-cil libgudev1.0-cil
libmono-sqlite2.0-cil: command not found
jennifer@jennifer-T3616:~$   libmono-wcf3.0-cil libgdiplus libnotify0.4-cil
libmono-wcf3.0-cil: command not found
jennifer@jennifer-T3616:~$ Use 'apt-get autoremove' to remove them.
Use: command not found
jennifer@jennifer-T3616:~$ The following extra packages will be installed:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
jennifer@jennifer-T3616:~$   libhd16
libhd16: command not found
jennifer@jennifer-T3616:~$ The following NEW packages will be installed:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
jennifer@jennifer-T3616:~$   hwinfo libhd16
oops: don't know what to do with "libhd16"
jennifer@jennifer-T3616:~$ 0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
0: command not found
jennifer@jennifer-T3616:~$ Need to get 744kB of archives.
No command 'Need' found, did you mean:
 Command 'seed' from package 'seed' (universe)
Need: command not found
jennifer@jennifer-T3616:~$ After this operation, 2,060kB of additional disk space will be used.
After: command not found
jennifer@jennifer-T3616:~$ Do you want to continue [Y/n]? y
Do: command not found
jennifer@jennifer-T3616:~$ Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe libhd16 i386 16.0-2 [698kB]
Get:1: command not found
jennifer@jennifer-T3616:~$ Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe hwinfo i386 16.0-2 [46.1kB]                                                                        
Get:2: command not found
jennifer@jennifer-T3616:~$ Fetched 744kB in 6s (107kB/s)                                                                                                                                
bash: syntax error near unexpected token `('
jennifer@jennifer-T3616:~$ Selecting previously deselected package libhd16.
Selecting: command not found
jennifer@jennifer-T3616:~$ (Reading database ... 177315 files and directories currently installed.)
Reading: command not found
jennifer@jennifer-T3616:~$ Unpacking libhd16 (from .../libhd16_16.0-2_i386.deb) ...
bash: syntax error near unexpected token `('
jennifer@jennifer-T3616:~$ Selecting previously deselected package hwinfo.
Selecting: command not found
jennifer@jennifer-T3616:~$ Unpacking hwinfo (from .../hwinfo_16.0-2_i386.deb) ...
bash: syntax error near unexpected token `('
jennifer@jennifer-T3616:~$ Processing triggers for man-db ...
Processing: command not found
jennifer@jennifer-T3616:~$ Setting up libhd16 (16.0-2) ...
bash: syntax error near unexpected token `('
jennifer@jennifer-T3616:~$ Setting up hwinfo (16.0-2) ...
bash: syntax error near unexpected token `('
jennifer@jennifer-T3616:~$ Processing triggers for libc-bin ...
Processing: command not found
jennifer@jennifer-T3616:~$ ldconfig deferred processing now taking place
/sbin/ldconfig.real: relative path `deferred' used to build cache
jennifer@jennifer-T3616:~$ jennifer@jennifer-T3616:~$ 
jennifer@jennifer-T3616:~$: command not found
jennifer@jennifer-T3616:~$

---

### Post by alexis44 on 2011-05-23
It doesn't work any differently.  :):)

---

### Post by linuxinstalledfromhdd on 2011-05-23
Let's try this a different way. 

What kind of system are you running?  What version of Ubuntu have you installed? How did you install it? Wubi? From a disc? From a USB stick?

---

### Post by alexis44 on 2011-05-23
> **linuxinstalledfromhdd said:**
> Let's try this a different way. 

What kind of system are you running?  What version of Ubuntu have you installed? How did you install it? Wubi? From a disc? From a USB stick?
I have an emachine.and I installed with a CD live disk of 10.10.  That's all I know. :)

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did this problem exist when you ran the live installation disc of Ubuntu?  Was the mouse acting strange while you were first using the live disc, and you were logged into the live version of Ubuntu on that disc?  Or is something that developed over time?

---

### Post by alexis44 on 2011-05-23
> **linuxinstalledfromhdd said:**
> Did this problem exist when you ran the live installation disc of Ubuntu?  Was the mouse acting strange while you were first using the live disc, and you were logged into the live version of Ubuntu on that disc?  Or is something that developed over time?
I installed in February and have of now, the last week or so, found the problem. :)

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did you upgrade to 11.04 or are you still using Ubuntu 10.10 Maverick?

---

### Post by alexis44 on 2011-05-23
I didn't upgrade.  I'm still using 10.10.

---

### Post by alexis44 on 2011-05-23
I would still like some help if anyone out there can! :)

---

### Post by alexis44 on 2011-05-31
I know that this is an old thread, and I'm sorry to bump it, I was wondering if someone could help me with it..

---

