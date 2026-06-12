---
title: "Remote Desktop not working under 9.10"
date: 2009-11-05
forum: General Help
---

### Post by werewolves on 2009-11-05
Ubuntu 9.10 64bit - Desktop effects enabled - remote desktop enabled, set to allow users to connect:

All I am able to see with a VNC client (KRDC or Chicken of the VNC) is a black screen.  I can see the machine, and the client connects, but I just get a black screen.

This used to work for me, but has been getting worse with each release.  Under 8.10, I was able to fully control my desktop, I just got a few visual artifacts while it was switching desktops with effects.  Under 9.04, I was able to see my desktop, but even though I checked that it was set to allow users to control the desktop, nothing would happen when I clicked.  With 9.10, just a black screen.

Sooo, any ideas?

---

### Post by werewolves on 2009-11-05
bump

---

### Post by werewolves on 2009-11-06
Anyone?  Pretty please...

---

### Post by XCan on 2009-11-06
I don't think they fixed the VNC with Compiz enabled. If you want to use VNC you have to disable Compiz. I agree, it's rediculess to ignore this issue, especially when there have been patches out for xorg for quite some time before the release of Jaunty. [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

---

### Post by Tony Ricena on 2009-11-06
I have something similar happening with mine, but i at least get the desktop on my connection and mouse, but nothing else.  But its funny if I reverse the remote connection.. from my desktop to laptop everything works great and I do have compiz enabled.  Its frustrating because I really need to use VNC for my dad when he has a problem

---

### Post by werewolves on 2009-11-07
Thanks for the link to the bug, I found a work-around at least, it's not perfect, but I can control the desktop again!

"A gconf option (/desktop/gnome/remote_session/disable_xdamage) has been added to disable the xdamage extension which is a temporary workaround although it requires more bandwidth. Enable the option through gconf-editor."

---

### Post by SiliconS on 2010-02-04
> **werewolves said:**
> Thanks for the link to the bug, I found a work-around at least, it's not perfect, but I can control the desktop again!

"A gconf option (/desktop/gnome/remote_session/disable_xdamage) has been added to disable the xdamage extension which is a temporary workaround although it requires more bandwidth. Enable the option through gconf-editor."
Awesome - thank you for posting this solution, werewolves. That was a big help for me.

---

