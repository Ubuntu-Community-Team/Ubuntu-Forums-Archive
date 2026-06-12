---
title: "Virtual Boot"
date: 2009-07-17
forum: General Help
---

### Post by nirgal2002 on 2009-07-17
I have a strange question for the forum. Is it possible to virtually boot a Windows system in a shell while in Ubuntu (any variant)? For example, booting from Ubuntu on CD/DVD/USB/etc, launching a shell window that boots the computers native OS (Windows XP for example) with the capability of debugging the native machine OS.

---

### Post by blueridgedog on 2009-07-17
Easily with vmware or virtualbox (or a few others).  I use Sun's Virtualbox.

I installed mine along the lines documented here:

[http://www.rasyid.net/2008/11/20/install-virtualbox-on-ubuntu-intrepid-lbex/](http://www.rasyid.net/2008/11/20/install-virtualbox-on-ubuntu-intrepid-lbex/)

---

### Post by nirgal2002 on 2009-07-17
Don't you have to go through a conversion first with vmware and virtualbox?  Trying to come up with the simplest solution that doesn't require converting the machine's drive as the first step.

---

### Post by blueridgedog on 2009-07-17
Ah...so you have a bootable installation on another partition that you want to start within a virtual window.

vmware has the ability (I have been told, not not practiced) that can do that.  I usually install images to virtualbox with install media so the OS is clean and simple.

---

### Post by nirgal2002 on 2009-07-17
That would be my normal approach as well.  However when trying to investigate a problem, doing a remote debug on a dirty machine is desired.  I'm merely trying to come up with a different approach to that by way of virtualization.

---

