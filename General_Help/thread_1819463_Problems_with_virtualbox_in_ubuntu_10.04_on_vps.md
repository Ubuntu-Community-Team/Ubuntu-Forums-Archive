---
title: "Problems with virtualbox in ubuntu 10.04 on vps"
date: 2011-08-06
forum: General Help
---

### Post by E2Razor on 2011-08-06
Hello,

I have done a lot of research but didn't find any solution for this problem. Or is it even possible to run it on vps with vncserver?
I have a vps server which had a ubuntu server 10.04 at first. Then I installed a ubuntu desktop and tightvncserver on it via terminal. Desktop and vncserver work fine. I have also installed VirtualBox OSE 3.1.6, kernel module sources for dkms and base binaries.
When i'm trying to run virtual XP I get Kernel driver is not installed (rc=-1908) error.
And it says I have to execute modprobe vboxdrv as a root. I have tried that also but then I get: 
Xlib: extension "RANDR" is missing on display ":1.0".
WARNING: Deprecated config file /ect/modprobe.conf, all config files belong into /ect/modprobe.d/
FATAL: Module vboxrdv not found.

I hope that I get some help please!
Thanks!

---

