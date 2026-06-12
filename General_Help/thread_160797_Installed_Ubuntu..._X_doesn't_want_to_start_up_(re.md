---
title: "Installed Ubuntu... X doesn't want to start up (resolution problem)"
date: 2006-04-15
forum: General Help
---

### Post by jazzyjayx on 2006-04-15
Hey all,

So I downloaded the Ubuntu 5.10 install CD and installed it on my system (on a virtual machine using Microsoft Virtual Server).

The install went fine, and it presented no errors. However, when it came time to boot up for the first time, the screen was full of errors. I suspect I chose a resolution during install that *something* didn't like.

My question... does anyone know if this is common? How can I choose what resolution to run at from within a command prompt? (I can get to a command prompt just fine).

I appreciate the help.

---

### Post by Zimmer on 2006-04-15
Firstly, I have no experience of trying to boot Ubuntu through the method of a Virtual Machine but....
Sounds like you need to configure X (edit the xorg.conf file) to handle your particular graphics card. Which card do you have?

EDIT:
A quick way to get going may be to edit the file as described here:
[http://ubuntuforums.org/showthread.php?t=160793](http://ubuntuforums.org/showthread.php?t=160793)

---

### Post by jazzyjayx on 2006-04-15
Here are some screenshots to show you guys exactly what my problem is.

[Booting up...](http://www.jayspang.com/pics/booting.jpg)
[Booting up later...](http://www.jayspang.com/pics/morebooting.jpg)
[Error once it tries to load X.](http://www.jayspang.com/pics/Error.jpg)

---

### Post by jazzyjayx on 2006-04-15
[QUOTE=Zimmer]Firstly, I have no experience of trying to boot Ubuntu through the method of a Virtual Machine but....
Sounds like you need to configure X (edit the xorg.conf file) to handle your particular graphics card. Which card do you have?[/QUOTE]ATI Radeon X800.

Where is the xorg.conf file located, and what can I use to edit it?

---

### Post by Zimmer on 2006-04-16
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
is the wiki I followed to get my ATI card to use 3d and it should come in handy for you too.

The xorg.conf file is at /etc/X11/xorg.conf
the command
sudo dpkg-reconfigure xserver-xorg
runs a Q&A utility for creating a config file
You can edit it by hand  using..

sudo nano /etc/X11/xorg.conf

copy it to a backup before you do that...

cp /etc/X11/xorg.conf  /etc/X11/xorg.bak

just in case...

---

