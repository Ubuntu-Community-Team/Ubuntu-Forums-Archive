---
title: "Upgraded to 11.04, freezes at login screen"
date: 2011-04-30
forum: General Help
---

### Post by tostrye on 2011-04-30
I just upgraded to 11.04. When I rebooted, everything looked normal. When it asked for my login credentials, it froze. I've tried recovery mode during grub selection, but no luck. I want to try 11.04! Help!

---

### Post by mokhan on 2011-05-01
I am having the same issue. I just upgraded from ubuntu 10.10 x64 to 11.04. After restarting to complete the update, it just freezes at the login screen. the keyboard and mouse is unresponsive, but the clock at the bottom right corner continues to update.

Don't make me use windows for the remainder of my holidays *sigh*

Please help!

---

### Post by ddm101 on 2011-05-01
Same problem here. I can, however, log in when I choose Ubuntu (with no effects) on the login screen. Even then, my PC will freeze if left unattended for a while; goes into sleep mode and becomes unresponsive.

---

### Post by techunit on 2011-05-01
Ok very simple solution. I can help all three of you.

First log-out and log-in to classic safe mode. Then go to settings admin additional drivers. Install the graphics drivers you need. Then reboot and start into Ubuntu Unity.

Good luck.

---

### Post by Anglagard on 2011-05-12
I fixed my login system freeze-ups by disabling CDEMU deamon /usr/lib/cdemu-daemon/cdemu-daemon.session on Ubuntu/Gnome application startup list by using safemode.

If you don't have CDEMU you can try disabling each application on the startup list and see which of them is causing a problem.
I logged out of safemode and back in for each app I disabled to find out the exact application that created the freeze-up.

Good luck!
Orion Vianna
My [blog at hackingmule.com]("http://blog.hackingmule.com")

---

