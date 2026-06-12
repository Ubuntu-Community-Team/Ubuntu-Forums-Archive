---
title: "Kubuntu VNC problem -- grey screen"
date: 2006-03-12
forum: General Help
---

### Post by mps75 on 2006-03-12
I'm trying to get VNC working on my Ubuntu box and have followed the steps outlined by Tichondrius in [ Gnome - HOWTO: Set up VNC server with resumable sessions]("http://www.ubuntuforums.org/showthread.php?t=122402&highlight=vnc").  I'm able to make a connection to VNC from my Windows box, but I only see a grey screen.  I've switched from kdm to gdm for my default display manager, but that hasn't helped.

Has anyone been able to get around this?  BTW, I'm running Ubuntu 5.10 "Breezy Badger".


thanks in advance,
matt

---

### Post by incubus on 2006-03-13
I haven't followed that tutorial myself, but I'd ask you:

1. Does this happen only in windows? Have you tried something like:
$ vncviewer localhost:1

2. Have you configured the files:
~/.vncrc
~/.vnc/xstartup

Particularly, the second is the one that should start your KDE session. I don't know if this applies to this case, but having a grey screen seems to point to that direction. You'd need to include something like "startkde" and perhaps edit the .vncrc to use the xstartup configuration. You can use /etc/vnc.conf as the model.

incubus

---

### Post by mps75 on 2006-03-13
The how-to didn't call for editing any of those files so initially I didn't.  However, I have tried modifying the /etc/vnc.conf file to use:

$vncStartup = "/home/mswanson/.vnc/xstartup";

rather than the default:
$vncStartup = "/etc/X11/Xsession";


Here's what I tried in my xstartup script (uncommenting one of the options at a time -- none of them worked):

#!/bin/sh

unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc
#startkde &
#gnome-session &


thanks for your help,
matt

---

### Post by dermotti on 2006-03-13
You should try FreeNX , it works out of the box after install and its much faster. 

[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

---

### Post by patrixl on 2006-03-13
This has been covered before, and 2 (or 3) solutions were found, do a search, here's what I remember:

solutions:

1 - use wdm instead of kdm (I did that till I found solution 2)
2 - upgrade to kde 3.5.1 (fixes KDM)
3 - (some other guy found this, I don't remember the exact details) uninstall kdm (kdebase-bin package maybe?) then reinstall kubuntu-desktop (after doing an apt-get update, of course, so you can get more recent packages which are fixed). Please make a search for topics concerning kdm, xdmcp, etc, to get the correct packages to uninstall/reinstall.

Patrix.

---

### Post by incubus on 2006-03-13
matt,

Strange, I have the same setup and it works correctly without any tweaking. The difference in my case is that I override /etc/vnc.conf with ~/.vncrc (I copied & renamed that file to my home directory).

Since you start with a grey screen, it seems that your xstartup is still not being called. Can you try that ~/.vncrc file? Also, I remember I had some issues with fonts not being found, do you get any errors like this?

incubus

EDIT: Reading what Patrix wrote, I'm inclined to agree that the problem should be KDM, since you're configuring it to be called first.

---

