---
title: "SAS 9.2 on Ubuntu"
date: 2009-10-28
forum: General Help
---

### Post by mörgæs on 2009-10-28
Finally I got SAS working on Ubuntu (8.10). Here is how:


**Hardware**

SAS 9.2 requires that the processor has SSE2. When running 
hwinfo --cpu 
this will show under 'Features' (assuming hwinfo is installed). 

Pentiums before 4 and a lot of older AMD-processors don't have SSE2. If this is the case, you don't have to read any further...



**Software**

The installation scripts requires bash, which is not the default shell in Ubuntu. If SAS's scripts explicitly called bash, the process would run on all Linux distros, but now Ubuntu and others must adapt to the script calling 'any shell' but silently demanding 'bash shell'. Let's hope that SAS will change this some day.

Until that a workaround is making bash the shell in Ubuntu:

sudo rm -f /bin/sh
sudo ln -s /bin/bash /bin/sh

More on this:
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)


If you for a while do not use SAS, it is possible to switch back to dash with

sudo rm -f /bin/sh
sudo ln -s /bin/dash /bin/sh


Switching globally to bash in stead of dash should in theory slow down the system, since bash is quite a bit larger, but I have not felt any difference. Some people report a much longer boot time, though.


In the installation directory of, say,
/usr/local/SAS/SASFoundation/9.2 
SAS is started with the command 

./sas -work /tmp/

since WORK is not assigned by default, as discussed in 
[http://support.sas.com/kb/17/783.html](http://support.sas.com/kb/17/783.html)


Happy hacking
/~mörgæs

---

### Post by albandy on 2009-10-28
Instead of creating and removing binaries and links use dpkg to configure the shell.

sudo dpkg-reconfigure dash

It will ask you what to use.

---

### Post by mörgæs on 2010-06-02
SAS 9.2 on Ubuntu 9.10:
[http://ubuntuforums.org/showthread.php?t=1494027](http://ubuntuforums.org/showthread.php?t=1494027)

---

