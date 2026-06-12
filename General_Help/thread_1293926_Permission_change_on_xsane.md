---
title: "Permission change on xsane"
date: 2009-10-17
forum: General Help
---

### Post by Joe_Linux on 2009-10-17
I am trying to access my scanner as a normal user (I can only so it as the root user now) when I try to change permission for that I get:

joe53@joe53-desktop:~$ sudo chmod 777 xsane
[sudo] password for joe53: 
chmod: cannot access `xsane': No such file or directory
joe53@joe53-desktop:~$ 

I am running Ubuntu 8.04
Thank you Joe

---

### Post by kbielefe on 2009-10-17
First of all, changing the permissions on the xsane executable isn't what you want.  If it *were* what you wanted, you would need to use the full path of /usr/bin/xsane.  Also if it were what you wanted, you would want 755 instead of 777.  777 will let anyone change xsane to do something else. Just want you to know for future reference.

You also don't want to run xsane as root if you can help it, so let's see if we can figure this out.  What we need to do is give you permissions for the scanner *device.  *Can you post the results of the following commands?

```
$ sudo scanimage -f "device %d model %m"
$ groups
```

---

### Post by Joe_Linux on 2009-10-17
kbielefe
Thank you for responding to my post. 

joe53@joe53-desktop:~$ sudo scanimage -f "device %d model %m"
[sudo] password for joe53: 
sudo: scanimage: command not found
joe53@joe53-desktop:~$ groups
joe53 adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare
joe53@joe53-desktop:~$

---

### Post by kbielefe on 2009-10-17
Try "sudo apt-get install sane-utils" and run the first one again, please.

---

### Post by Joe_Linux on 2009-10-18
joe53@joe53-desktop:~$ sudo apt-get install sane-utils
[sudo] password for joe53: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  unpaper
The following NEW packages will be installed:
  sane-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 136kB of archives.
After this operation, 365kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe sane-utils 1.0.19-1ubuntu3 [136kB]
Fetched 136kB in 1s (78.1kB/s)    
Selecting previously deselected package sane-utils.
(Reading database ... 127724 files and directories currently installed.)
Unpacking sane-utils (from .../sane-utils_1.0.19-1ubuntu3_amd64.deb) ...
Setting up sane-utils (1.0.19-1ubuntu3) ...
Adding saned group and user...

joe53@joe53-desktop:~$ sudo scanimage -f "device %d model %m"
device microtek:/dev/sg2 model ScanMaker E3joe53@joe53-desktop:~$ 

The result

---

### Post by kbielefe on 2009-10-18
Okay, good.  Now:

```
$ ls -l /dev/sg2
```

---

### Post by Joe_Linux on 2009-10-18
joe53@joe53-desktop:~$ ls -l /dev/sg2
crw-rw---- 1 root cdrom 21, 2 2009-10-18 17:38 /dev/sg2
joe53@joe53-desktop:~$ 
 
The result

---

### Post by kbielefe on 2009-10-18
Strange.  It looks like you already have permission on the device.  What exactly is the error you're getting when not running as root?  Can you do a "ls -l /usr/bin/xsane" ?

---

### Post by Joe_Linux on 2009-10-18
joe53@joe53-desktop:~$ ls -l /usr/bin/xsane
-rwxr-xr-x 1 root root 643712 2007-12-03 03:12 /usr/bin/xsane
joe53@joe53-desktop:~$ 

I open Xsane and I get the message "no devices avaiable"

---

### Post by Joe_Linux on 2009-10-18
Please see attached image in answer to your question

---

### Post by kbielefe on 2009-10-19
95% of the time, it would already be working for you just by having the correct permissions on the device.  Let's cast the net a little wider and see if we can catch something.  Try:

```
$ xsane /dev/sg2
$ xsane microtek:/dev/sg2
$ ls -l /etc/sane.d/microtek.conf
$ cat /etc/sane.d/microtek.conf
$ ls -l /usr/lib/sane/*microtek*
$ dmesg
```Also try adding a line that says /dev/sg2 to /etc/sane.d/microtek.conf, if it isn't already there.

---

### Post by Joe_Linux on 2009-10-20
kbielefe

xsane /dev/sg2  see attached file sg2.xcf for result

xsane microtek:/dev/sg2  see attached file microtrk.xcf for result

joe53@joe53-desktop:~$ ls -l /etc/sane.d/microtek.conf
-rw-r--r-- 1 root root 277 2009-10-19 18:16 /etc/sane.d/microtek.conf
joe53@joe53-desktop:~$ 

joe53@joe53-desktop:~$ cat /etc/sane.d/microtek.conf
# Uncomment following line to disable "real calibration" routines...
#norealcal
# Uncomment following line to disable "clever precalibration" routines...
#noprecal
#   Using "norealcal" will revert backend to pre-0.11.0 calibration code.
scsi * * Scanner
/dev/scanner
/dev/sg2
joe53@joe53-desktop:~$ 

As you can see I added /dev/sg2 (can still not find scanner as normal user)

joe53@joe53-desktop:~$ ls -l /usr/lib/sane/*microtek*
-rw-r--r-- 1 root root    868 2008-03-25 10:38 /usr/lib/sane/libsane-microtek2.la
lrwxrwxrwx 1 root root     27 2009-05-12 16:39 /usr/lib/sane/libsane-microtek2.so.1 -> libsane-microtek2.so.1.0.19
-rw-r--r-- 1 root root 126160 2008-03-25 10:38 /usr/lib/sane/libsane-microtek2.so.1.0.19
-rw-r--r-- 1 root root    861 2008-03-25 10:38 /usr/lib/sane/libsane-microtek.la
lrwxrwxrwx 1 root root     26 2009-05-12 16:39 /usr/lib/sane/libsane-microtek.so.1 -> libsane-microtek.so.1.0.19
-rw-r--r-- 1 root root  85272 2008-03-25 10:38 /usr/lib/sane/libsane-microtek.so.1.0.19
joe53@joe53-desktop:~$

---

### Post by Joe_Linux on 2009-10-20
whe I try to include the result of dmesg  I get 
You have included 9 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

---

### Post by Dennis N on 2009-10-20
Your post #3 results don't show you are in the 'scanner' group. If you haven't done so, you need to add yourself to that group to use a scanner.

---

### Post by kbielefe on 2009-10-20
> **Dennis N said:**
> Your post #3 results don't show you are in the 'scanner' group. If you haven't done so, you need to add yourself to that group to use a scanner.

Well, not necessarily.  My systems don't even *have* a scanner group, jaunty on my laptop and karmic on the desktop with the scanner, and the device returned by scanimage was using the cdrom group, which *is *listed.  Can't hurt to add him to the scanner group if his system has it, though.

Looks like root may have been using /dev/scanner instead of /dev/sg2.  Try:

```

$ ls -l /dev/scanner
$ dmesg > dmesg.txt

```Attach the dmesg.txt file.  It will be text instead of an image.

---

### Post by Joe_Linux on 2009-10-22
dmesg.txt:
Your file of 25.3 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.
 

joe53@joe53-desktop:~$ ls -l /dev/scanner
ls: cannot access /dev/scanner: No such file or directory

---

### Post by kbielefe on 2009-10-22
Try "gzip dmesg.txt" then attach the .gz file.

---

### Post by Joe_Linux on 2009-10-22
kbielefe

Here is the dmesg finally

---

### Post by kbielefe on 2009-10-22
Okay, the dmesg shows the scanner on /dev/sg0, not sg2, so try adding that to /etc/sane.d/microtek.conf and do an "ls -l /dev/sg0" to make sure you are in the right group ("sudo usermod -aG whatevergroup joe53" if not).  Sorry this is taking so much back and forth.  We are *that close*, I can feel it.

---

### Post by Joe_Linux on 2009-10-23
kbielefe

joe53@joe53-desktop:~$ cat /etc/sane.d/microtek.conf
# Uncomment following line to disable "real calibration" routines...
#norealcal
# Uncomment following line to disable "clever precalibration" routines...
#noprecal
# Using "norealcal" will revert backend to pre-0.11.0 calibration code.
scsi * * Scanner
/dev/scanner
/dev/sg2
joe53@joe53-desktop:~$

As you can see I added /dev/sg2 (can still not find scanner as normal user)

joe53@joe53-desktop:~$ ls -l /dev/sg0
crw-rw---- 1 root cdrom 21, 0 2009-10-22 15:35 /dev/sg0
joe53@joe53-desktop:~$ 

kbielefe 
I am not certain on how to use the above info to tell if I am correct group. sorry :(

---

### Post by kbielefe on 2009-10-23
Still shows you in the correct group (the cdrom from this command showed up on your groups command).  Try this next:

```
$ strace -eopen xsane microtek:/dev/sg0 2>&1 | grep /dev/sg
```

---

### Post by Joe_Linux on 2009-10-23
joe53@joe53-desktop:~$ strace -eopen xsane microtek:/dev/sg0 2>&1 | grep /dev/sg
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 7
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 7
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_EXCL|O_NONBLOCK) = 7
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 7
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 7
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = 8
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg0", O_RDWR|O_EXCL|O_NONBLOCK) = -1 EACCES (Permission denied)
joe53@joe53-desktop:~$

---

### Post by Joe_Linux on 2009-10-23
kbielefe  	
the error message came up also

---

### Post by kbielefe on 2009-10-23
Okay, this is just getting bizarre.  Just as a sanity check, run the following.  If it fixes it, it will only fix it until the next reboot, and will allow any user on your system to mess with the scanner temporarily, but will at least let us know if we are barking up the right tree.

```
$ groups
$ sudo chmod 777 /dev/sg0
$ lsof | grep /dev/sg0
$ strace xsane microtek:/dev/sg0 2>&1 | grep "= -1"
```

---

### Post by Joe_Linux on 2009-10-25
Sorry I did not post sooner
joe53@joe53-desktop:~$ groups
joe53 adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare
joe53@joe53-desktop:~$ sudo chmod 777 /dev/sg0
[sudo] password for joe53: 
joe53@joe53-desktop:~$ lsof | grep /dev/sg0
joe53@joe53-desktop:~$ 
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/etc/ieee1284.conf", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/parport0", O_RDONLY|O_NOCTTY) = -1 EACCES (Permission denied)
open("/dev/parports/0", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport1", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parports/1", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport2", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parports/2", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport3", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parports/3", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport4", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parports/4", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport5", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parports/5", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport6", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parports/6", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport7", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parports/7", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
ioperm(0x378, 0x3, 0x1)                 = -1 EPERM (Operation not permitted)
open("/dev/port", O_RDWR|O_NOCTTY)      = -1 EACCES (Permission denied)
open("/dev/lp0", O_RDONLY|O_NOCTTY)     = -1 EACCES (Permission denied)
open("/dev/lp1", O_RDONLY|O_NOCTTY)     = -1 ENOENT (No such file or directory)
open("/dev/lp2", O_RDONLY|O_NOCTTY)     = -1 ENOENT (No such file or directory)
open("/dev/lp3", O_RDONLY|O_NOCTTY)     = -1 ENOENT (No such file or directory)
open("/dev/lp4", O_RDONLY|O_NOCTTY)     = -1 ENOENT (No such file or directory)
open("/dev/lp5", O_RDONLY|O_NOCTTY)     = -1 ENOENT (No such file or directory)
open("/dev/lp6", O_RDONLY|O_NOCTTY)     = -1 ENOENT (No such file or directory)
open("/dev/lp7", O_RDONLY|O_NOCTTY)     = -1 ENOENT (No such file or directory)
open("./microtek2.conf", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./microtek.conf", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner/", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_EXCL|O_NONBLOCK) = -1 EACCES (Permission denied)
open("./matsushita.conf", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff10)       = -1 ENOENT (No such file or directory)
open("./ma1509.conf", O_RDONLY)         = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff20)       = -1 ENOENT (No such file or directory)
open("./lexmark.conf", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("./leo.conf", O_RDONLY)            = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./ibm.conf", O_RDONLY)            = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./hs2p.conf", O_RDONLY)           = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191c0f70)       = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191c0f50)       = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff30)       = -1 ENOENT (No such file or directory)
open("./hp5400.conf", O_RDONLY)         = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff50)       = -1 ENOENT (No such file or directory)
open("./hp4200.conf", O_RDONLY)         = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191c0f70)       = -1 ENOENT (No such file or directory)
open("./hpsj5s.conf", O_RDONLY)         = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff30)       = -1 ENOENT (No such file or directory)
open("./hp3900.conf", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("./hp.conf", O_RDONLY)             = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bbec0)       = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bfed0)       = -1 ENOENT (No such file or directory)
open("./gt68xx.conf", O_RDONLY)         = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff30)       = -1 ENOENT (No such file or directory)
open("./genesys.conf", O_RDONLY)        = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191c0f70)       = -1 ENOENT (No such file or directory)
open("./fujitsu.conf", O_RDONLY)        = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff20)       = -1 ENOENT (No such file or directory)
open("./epson.conf", O_RDONLY)          = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff40)       = -1 ENOENT (No such file or directory)
open("./epjitsu.conf", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("./dmc.conf", O_RDONLY)            = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/camera", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./dell1600n_net.conf", O_RDONLY)  = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191c0f70)       = -1 ENOENT (No such file or directory)
open("./coolscan2.conf", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("./coolscan.conf", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191c0f70)       = -1 ENOENT (No such file or directory)
open("./cardscan.conf", O_RDONLY)       = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff50)       = -1 ENOENT (No such file or directory)
open("./canon630u.conf", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("./canon.conf", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./bh.conf", O_RDONLY)             = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
stat("/usr/local/sbin/as6edriver", 0x7fff191c12c0) = -1 ENOENT (No such file or directory)
stat("/usr/local/bin/as6edriver", 0x7fff191c12c0) = -1 ENOENT (No such file or directory)
stat("/usr/sbin/as6edriver", 0x7fff191c12c0) = -1 ENOENT (No such file or directory)
stat("/usr/bin/as6edriver", 0x7fff191c12c0) = -1 ENOENT (No such file or directory)
stat("/sbin/as6edriver", 0x7fff191c12c0) = -1 ENOENT (No such file or directory)
stat("/bin/as6edriver", 0x7fff191c12c0) = -1 ENOENT (No such file or directory)
stat("/usr/games/as6edriver", 0x7fff191c12c0) = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191beeb0)       = -1 ENOENT (No such file or directory)
open("./artec_eplus48u.conf", O_RDONLY) = -1 ENOENT (No such file or directory)
open("./artec.conf", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
stat("/dev/usb/", 0x7fff191bff10)       = -1 ENOENT (No such file or directory)
open("./avision.conf", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("./apple.conf", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./agfafocus.conf", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./abaton.conf", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/scsi/host4/bus0/target6/lun0/generic", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg1", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg5", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/sg6", O_RDWR|O_NONBLOCK)     = -1 ENOENT (No such file or directory)
open("/dev/scanner", O_RDWR|O_EXCL|O_NONBLOCK) = -1 ENOENT (No such file or directory)
open("./net.conf", O_RDONLY)            = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/dev/bus/usb/005/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(7, USBDEVFS_CONNECTINFO, 0x7fff191bad40) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/005/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(6, USBDEVFS_IOCTL, 0x7fff191bcd00) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/004/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(7, USBDEVFS_CONNECTINFO, 0x7fff191bad40) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/004/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(6, USBDEVFS_IOCTL, 0x7fff191bcd00) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/003/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(7, USBDEVFS_CONNECTINFO, 0x7fff191bad40) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/003/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(6, USBDEVFS_IOCTL, 0x7fff191bcd00) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/002/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(7, USBDEVFS_CONNECTINFO, 0x7fff191bad40) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/002/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(6, USBDEVFS_IOCTL, 0x7fff191bcd00) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/001/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(7, USBDEVFS_CONNECTINFO, 0x7fff191bad40) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/001/001", O_RDWR)    = -1 EACCES (Permission denied)
ioctl(6, USBDEVFS_IOCTL, 0x7fff191bcd00) = -1 EPERM (Operation not permitted)
open("/dev/bus/usb/005/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/004/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/003/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/002/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/001/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/parport0", O_RDONLY|O_NOCTTY) = -1 EACCES (Permission denied)
open("/dev/parport1", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport2", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/dev/parport3", O_RDONLY|O_NOCTTY) = -1 ENOENT (No such file or directory)
open("/home/joe53/.cups/client.conf", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/joe53/.cupsrc", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/etc/cups/client.conf", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/joe53/.cups/client.conf", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/joe53/.cupsrc", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/etc/cups/client.conf", O_RDONLY) = -1 ENOENT (No such file or directory)
connect(6, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
connect(6, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/x86_64/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/lib/tls/x86_64", 0x7fff191bc840) = -1 ENOENT (No such file or directory)
open("/lib/tls/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/lib/tls", 0x7fff191bc840)        = -1 ENOENT (No such file or directory)
open("/lib/x86_64/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64", 0x7fff191bc840)     = -1 ENOENT (No such file or directory)
open("/lib/libnss_db.so.2", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/usr/lib/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/x86_64/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls/x86_64", 0x7fff191bc840) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/tls/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/tls", 0x7fff191bc840) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/x86_64/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/lib/x86_64-linux-gnu/x86_64", 0x7fff191bc840) = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/x86_64/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls/x86_64", 0x7fff191bc840) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/tls/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/tls", 0x7fff191bc840) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/x86_64/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat("/usr/lib/x86_64-linux-gnu/x86_64", 0x7fff191bc840) = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libnss_db.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
setsockopt(7, SOL_TCP, TCP_NODELAY, [1], 4) = -1 EOPNOTSUPP (Operation not supported)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(5, 0x6be4f4, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
joe53@joe53-desktop:~$ 

As you mentioned it does open it till I reboot

---

