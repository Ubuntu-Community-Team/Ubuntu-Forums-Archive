---
title: "Ubuntu / Windows boot sequence"
date: 2011-01-08
forum: General Help
---

### Post by cancer10 on 2011-01-08
Hi

Is there anyway in ubuntu I can set the boot sequence of the different OS that appear as a list when I boot my machine?

I used to do this using MSCONFIG in Windows but for some reason I cannot do this in this current machine I am working on.

So can this be done on Ubuntu 10.04?

Any help s appreciated.

---

### Post by cancer10 on 2011-01-15
anyone?


thanx

---

### Post by marin123 on 2011-01-15
```
sudo apt-get install startupmanager
```

after you install this package, run it and the rest should be pretty straightforward :)

you cannot edit boot sequence in msconfig because windows bootloader is only loading windows while ubuntu bootloader (GRUB) is loading both - windows and ubuntu.

---

### Post by cancer10 on 2011-01-15
> **marin123 said:**
> ```
sudo apt-get install startupmanager
```

after you install this package, run it and the rest should be pretty straightforward :)

you cannot edit boot sequence in msconfig because windows bootloader is only loading windows while ubuntu bootloader (GRUB) is loading both - windows and ubuntu.

Thanks Marin123

I did installed it but it does not appear anywhere under the applications menu. Where do i fnd it?

thnaks

---

### Post by wilee-nilee on 2011-01-15
> **cancer10 said:**
> Thanks Marin123

I did installed it but it does not appear anywhere under the applications menu. Where do i fnd it?

thnaks

Should be in system preferences or admin. Right click the menu if not found then edit and see if the program needs to be ticked off then on, sometimes a fresh install doesn't show as it should immediately.

---

### Post by cancer10 on 2011-01-15
hi

I get the following error when i launch startupmanager

> An error occurred while loading or saving configuration information for startupmanager. Some of your configuration settings may not work properly.

> 
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)



Is this normal?

---

### Post by cancer10 on 2011-01-15
ok nevermind that error. I get it only when i launch the startup manager from the command line.

> **wilee-nilee said:**
> Should be in system preferences or admin. Right click the menu if not found then edit and see if the program needs to be ticked off then on, sometimes a fresh install doesn't show as it should immediately.

I made ubuntu as my default OS but when I reboot, it shows windows as my default OS.

Pls see the attached screenshot.

---

### Post by marin123 on 2011-01-15
when you run it, does it say that its peforming some pre-configuration, and when you close, does it configure something again? if you cannot customize grub with this, i recommend grub-customizer:

[HTML]https://launchpad.net/grub-customizer[/HTML]

on your screenshot, it says you have 5 second timeout. is that correct? does grub have 5 sec timeout?

---

### Post by marin123 on 2011-01-15
when you run it, does it say that its peforming some pre-configuration, and when you close, does it configure something again? if you cannot customize grub with this, i recommend grub-customizer:

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

on your screenshot, it says you have 5 second timeout. is that correct? does grub have 5 sec timeout?

---

### Post by cancer10 on 2011-01-15
> **marin123 said:**
> when you run it, does it say that its peforming some pre-configuration, and when you close, does it configure something again? if you cannot customize grub with this, i recommend grub-customizer:

[HTML]https://launchpad.net/grub-customizer[/HTML]

on your screenshot, it says you have 5 second timeout. is that correct? does grub have 5 sec timeout?

That 5 second timeout was set by me, the default was 10 secs.

Even aftr reading the intro text on their site, i still could not understand what grub customizer does.

---

### Post by marin123 on 2011-01-15
install it and run it by pressing alt+f2 and type grub-customizer. thats another grub-editing application, maybe that helps...

---

