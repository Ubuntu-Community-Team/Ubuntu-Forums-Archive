---
title: "How to start-shutdown Ubuntu without GUI ?"
date: 2010-11-10
forum: General Help
---

### Post by kema_u on 2010-11-10
Hi!

I use Ubuntu 10.1(updated). I want to see the outputs (from the black screen) and not the GUI when i shutdown and open the Ubuntu
(But please don't using the GRUB features). Can someone please help me ?

Thank you!

---

### Post by sikander3786 on 2010-11-10
Hi.

> (But please don't using the GRUB features).

But I don't know if there is any other way of achieving it. You'll need to edit /etc/default/grub and remove quiet & splash and run update-grub. Post back if you intend to do it that way.

---

### Post by I'mGeorge on 2010-11-10
I believe there are two ways to do it. The simple way it would be to install a software named Start-Up manager. There as I remember it's an option show splash image on boot. Or another way would be to follow this handy tutorial where you can get rid of the splash screen temporarely or permanently [http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/)

---

### Post by kema_u on 2010-11-10
Startup manager can close the GUI when starts Ubuntu. But it will not work when i shut down it. 

I saw from the screenshot of software center for "boot up manager" which can makes "startup and shut down scripts". Can that solve my problem ? ( screenshot : [http://linux.softpedia.com/screenshots/BUM-Boot-Up-Manager_2.jpg](http://linux.softpedia.com/screenshots/BUM-Boot-Up-Manager_2.jpg) )

---

### Post by kema_u on 2010-11-13
Any help please ? :(

---

### Post by garvinrick4 on 2010-11-13
If you do not want a splash screen at boot up or shutdown you uninstall plymouth.
```
 
sudo apt-get remove plymouth

```EDIT: OP removed a plymouth theme not full plymouth package: 
Removed was post 9.
 
Post 7 seems like a way to create same outcome with editing config file instead of removing
a theme in plymouth.

---

### Post by Elfy on 2010-11-13
You need to remove quiet and splash as you've been told.

As this is set by grub - you'll need to do so.

```
gksudo gedit /etc/default/grub
```

find this line 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

change to 

```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

save 

update grub

```
sudo update-grub
```

---

### Post by kema_u on 2010-11-13
@garvinrick4 i can not delete plymouth because it removes all other packages on my computer. so i try to delete plymouth-ubuntu-theme-text and logo, now ubuntu is shutting down and opening by text. perfect. thank you ! :)

---

### Post by garvinrick4 on 2010-11-13
A thank you is nice but I was wrong it was a theme in plymouth not full plymouth:
Enjoy your Ubuntu kema_u

This is the package OP removed: A theme of plymouth not full plymouth:
```
rick@rick-laptop:~$ aptitude show plymouth-theme-ubuntu-text
Package: plymouth-theme-ubuntu-text
State: installed
Automatically installed: no
Version: 0.8.2-2ubuntu2.1
Priority: standard
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 94.2k
Depends: libc6 (>= 2.2.5), libplymouth2 (>= 0.8.0~-13~ppa1), plymouth
Replaces: plymouth (< 0.8.1-1~)
Provides: plymouth-theme
Description: graphical boot animation and logger - ubuntu-logo theme
 Plymouth is an application that runs very early in the boot process (even
 before the root filesystem is mounted!) that provides a graphical boot
 animation while the boot process happens in the background. 

```

---

