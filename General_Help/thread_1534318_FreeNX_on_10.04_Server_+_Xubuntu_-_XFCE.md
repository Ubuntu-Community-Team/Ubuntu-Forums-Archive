---
title: "FreeNX on 10.04 Server + Xubuntu - XFCE"
date: 2010-07-19
forum: General Help
---

### Post by xflyboy on 2010-07-19
Hello.
I would aprresiate some assistance on getting FreeNX to work properly on Lucid 10.04 Server instalation with xubuntu-desktop package installed.

What i intent to do is to run this PC - headless, remotely.
My main goal was to start this PC, get CONSOLE screen on main display at Server room (not Sesion Manager neither any graphical output) and connect to it remotely getting directly into XFCE Window manager.

I didn fresh instalation of Server, xubuntu-deskto, and freeNX (I followed [this]("https://help.ubuntu.com/community/FreeNX") UPDATED guide).
On client side i'm using "NX Client for Windows version 3.4.0.7"
The only way i found to log properly is to configure Client Settings/General/Desktop on UNIX - XDM (default options for that), and when i get initial Screen with small terminal prompt, i enter startxfce4 and i have complete graphical interface.

I would to have that automaticaly when i click connect on Client Side.

I belive that this would be posible modifying .xinitrc and Client Desktop option but not sure what.

Please assist.

Usefull links but some old some incomplete: 
[https://launchpad.net/~freenx-team/+archive/ppa](https://launchpad.net/~freenx-team/+archive/ppa)
[http://ubuntuforums.org/showthread.php?t=128374](http://ubuntuforums.org/showthread.php?t=128374)
[http://muzso.hu/2007/05/05/connecting-to-a-linux-server-to-xfce-using-freenx](http://muzso.hu/2007/05/05/connecting-to-a-linux-server-to-xfce-using-freenx)
[http://wiki.archlinux.org/index.php/FreeNX](http://wiki.archlinux.org/index.php/FreeNX)


[http://ubuntuforums.org/showthread.php?t=1470941&highlight=freenx+lucid+server](http://ubuntuforums.org/showthread.php?t=1470941&highlight=freenx+lucid+server)

---

### Post by xflyboy on 2010-07-21
Found it to be working with CUSTOM Desktop setting.
But i did it with another User ID.
[From Here.]("http://muzso.hu/2007/05/05/connecting-to-a-linux-server-to-xfce-using-freenx")

> I found that nxclient does not run any login shell
so that there are not run scripts from /etc/profile.d. My solution is command line:

/bin/bash -l /usr/bin/startxfce4

(or .... /usr/bin/xfce4-session if you wish).

Regards
pjo

---

### Post by xflyboy on 2010-07-21
I couldn't make it work with Original User, but i did with another clean user.
> #

Problem: At the client, the !M logo window appears, but after a few seconds that window just closes, even without showing any error message.
#

Solution: In the server, access your home directory and run this command, sudo rm .Xauthority* followed by touch .Xauthority and finally chmod 600 .Xauthority . This issue is due custom VNC configuration. 
Did not do the trick with original user. So i removed .Xauthority and folder .nx and it did.
Solved.

---

