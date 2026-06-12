---
title: "Broken System - Dist Upgrade"
date: 2010-08-21
forum: General Help
---

### Post by tarun86 on 2010-08-21
I was doing dist-upgrade when my brother switched off the system. Now the thing is apt at that moment was setting up the downloaded deb files. I could correct my system using a live cd but **at present my cd-drive is messed up. **[COLOR="Red"]***I have a windows partition working perfectly, can someone help me as to how to log into ubuntu environment from windows. ***[/COLOR]

All I need to do is - 
> dpkg --configure -a
but I dont know how to get into linux environment other than live cd which as I mentioned is not an option.

---

### Post by pastalavista on 2010-08-21
Does Grub load? Press and hold "Shift" while booting to access Grub and select "recovery mode". If Grub won't load, there's no way without a live CD or USB stick. You can download [Unetbootin]("http://unetbootin.sourceforge.net/") for Windows to make bootable USB flash drive of the Ubuntu live .iso and boot from it to repair your Ubuntu installation.

---

