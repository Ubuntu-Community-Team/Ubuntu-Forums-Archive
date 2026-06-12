---
title: "Ubuntu installed GRUB to my flash drive."
date: 2012-05-19
forum: General Help
---

### Post by Muffinabus on 2012-05-19
I've been away from Ubuntu for a while but decided to give it a go on my new computer.  I was creating a dual boot setup for Windows 7 (already installed) and 12.04 (both 64 bit).  I chose the automatic resize partition and install alongside Windows option.  Upon restarting the computer after the install had completed it boot straight into Windows.  I attempted to go back into the live USB to take a look at what happened when it popped up with GRUB and booted me into my Ubuntu install.

Is there any reason why this happened?  I wasn't given a choice on where to install GRUB in the automatic setup but why in the world would it default to my flash drive?  Is there an easy way to move this to my hard drive or would it be easier to wipe it clean now (while it's still new) and do a manual install telling GRUB to install to the hard drive?

---

### Post by wilee-nilee on 2012-05-19
Generally a easy fix, there is app called boot-repair, you can download a cd, or load it on a Ubinti live cd to run. I think the recommended repair should fix this.[https://help.ubuntu.com/community/Boot-RepairSome](https://help.ubuntu.com/community/Boot-RepairSome) times I have had a booted usb reverse the way the HD is read and the usb. The install should default to the sda hd(internal)but if reversed the sda is the usb.  boot-repair runs a bootscript when you use it so save the http address if you need more help, and post it if so.

---

