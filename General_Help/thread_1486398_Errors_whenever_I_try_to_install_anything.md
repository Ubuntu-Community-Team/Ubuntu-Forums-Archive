---
title: "Errors whenever I try to install anything"
date: 2010-05-17
forum: General Help
---

### Post by AlexRamallo on 2010-05-17
I've been trying to download the freeglut development files, but whenever I try(through synaptic package manager and terminal) I get this error:
> 
E: fglrx: subprocess installed post-removal script returned error exit status 2

but its not just that package, its ANYTHING.

The error started to arise(I think) when I tried to install the [_ATi catalyst display drivers_](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English) (since the ubuntu proprietary drivers made it lagg whenever I minimized/maximized windows)

I'm on Ubuntu 10.04 x64, and my gfx card is a Radeon HD 4670, if thats relevant
EDIT:
btw, I'm still a nooby linux user, so I might need a little extra help ;)

---

### Post by marshmallow1304 on 2010-05-17
Try
```
sudo apt-get -f install
```

Or open Synaptic and do Edit->Fix Broken Packages

---

### Post by AlexRamallo on 2010-05-17
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 100MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 163689 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
[B]Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
alex@alex-linux:~$ 

same problem, look at the last lines :(

btw just for curiosity, what does that command do? does it install anything in particular? cause it doesnt have a package name :confused:

---

### Post by marshmallow1304 on 2010-05-18
> **AlexRamallo said:**
> same problem, look at the last lines :(

btw just for curiosity, what does that command do? does it install anything in particular? cause it doesnt have a package name :confused:

It fixes broken packages (or attempts to).

Try
```
sudo dpkg --configure -a
```

---

### Post by AlexRamallo on 2010-05-18
when I put that command it didn't give any error or show any message, it just went to the next line, but I still get the error when trying to install stuff :(

> E: fglrx: subprocess installed post-removal script returned error exit status 2

---

### Post by AlexRamallo on 2010-05-19
no one can help me? :(

---

### Post by blue_print on 2010-05-19
Have a try with the steps mentioned in the following links. Hope, this will fix your issue.

[http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html](http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html)

[http://odzangba.wordpress.com/2009/10/14/how-to-fix-%E2%80%9Csubprocess-pre-removal-script-returned-error-exit-status-2%E2%80%B3-error/](http://odzangba.wordpress.com/2009/10/14/how-to-fix-%E2%80%9Csubprocess-pre-removal-script-returned-error-exit-status-2%E2%80%B3-error/)

[B][COLOR=DarkGreen]Blue Print[/COLOR]
Linux Admin/Helper[/B]

---

### Post by blue_print on 2010-05-19
Have you solved your problem?

---

### Post by AlexRamallo on 2010-05-19
nope not yet :(

I think its trying to delete a script or something called fglrx but gets an error when trying to remove it..not sure just a guess

i dont want to have to reinstall ubuntu, doesn't anyone have an answer to this? TT_TT

---

### Post by ablebaker on 2010-05-22
Does this post resolve your issue:

[http://ubuntuforums.org/showpost.php?p=5280641&postcount=5](http://ubuntuforums.org/showpost.php?p=5280641&postcount=5)

---

### Post by Willard on 2011-05-08
I had this same problem, after upgrading to a new major release (10.04 to 10.10).

That last suggestion by ablebaker worked for me (all the other suggestions did not).

---

