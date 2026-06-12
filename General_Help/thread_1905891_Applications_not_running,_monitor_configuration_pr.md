---
title: "Applications not running, monitor configuration problem, and more graphics troubles"
date: 2012-01-07
forum: General Help
---

### Post by electrojustin on 2012-01-07
Ok, let me start from the beginning. So I had this problem with my webcam and I thought perhaps recompiling the kernel would work. After much trial and error, several tutorials and three days I got a working^W bootable kernel. I noticed that fglrx wasn't working properly and graphically intense applications weren't running at all (can't remember the error code and can't check my browser history for it for reasons that will soon be apparent). I attempted to uninstall fglrx and install fglrx-amdcccle-updates and fglrx-updates to fix this problem. Unfortunately I came across an error when installing fglrx-updates. It follows: ```
(Reading database ... 251612 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb) ...
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
dpkg: error processing /var/cache/apt/archives/fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx-updates_2%3a8.911-0ubuntu0.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I have two monitors by the way. My left of which currently is not receiving input and is idle. Certain applications don't run (e.g. chromium) and there seems to be desktop to the right of my right monitor, which I obviously can't reach. Panel 2 is half hidden and completely askew (I use xfce but I doubt the problem is directly related to that, hence the prefix). Those aren't the only things wrong, but I can't think of a complete list at the moment.
As you can see I really have no idea what I'm doing. Should I just reload and be done with it? Please help.

---

### Post by wildmanne39 on 2012-01-07
Hi, in my opinion if you are having several problems after recompiling the kernel it would probably be easier to reinstall because you may have made several changes to it and that makes troubleshooting almost impossible.> One or more files have been altered since installation.
Uninstall will not be completedis probably just the beginning of your issues.
Thanks

---

### Post by bluexrider on 2012-01-08
That just doesn't look right. Think I would consider reinstall. Make sure you back your files before doing that. Good luck

---

### Post by electrojustin on 2012-01-08
Actually I don't think the kernel was the problem. You see I actually dual booted the kernels rather than replacing one with the other. Also, before I rebooted to test the other kernel I got a kernel panic from the generic one that seemed to involve fglrx. Well the screen is completely black now so no option but to reinstall. Thanks for the help!

---

### Post by electrojustin on 2012-01-08
On second thought the kernel was the only thing I changed. ;)

---

### Post by wildmanne39 on 2012-01-08
Hi, if you can get into the grub menu, you should be able to use these commands to reset x.org file:
```
sudo rm /etc/X11/xorg.conf
```  
```
sudo dpkg-reconfigure xserver-xorg
```
but if you are still having system wide issues reinstalling may be the quickest way to fix them but if list all the problems you were referring to someone maybe able to help with those.
> I have two monitors by the way. My left of which currently is not receiving input and is idle. Certain applications don't run (e.g. chromium) and there seems to be desktop to the right of my right monitor, which I obviously can't reach. Panel 2 is half hidden and completely askew (I use xfce but I doubt the problem is directly related to that, hence the prefix). Those aren't the only things wrong, but I can't think of a complete list at the moment. 
Unless they are related you should list one issue per thread, it makes it easier to help that way.
Thanks

---

