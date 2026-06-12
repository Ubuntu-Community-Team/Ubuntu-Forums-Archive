---
title: "ati dual monitors on 10.04 Gnome"
date: 2010-05-04
forum: General Help
---

### Post by whatch on 2010-05-04
I have a ATI VisionTek 9250 128mb DMS59 PCI video card that I would like to use for dual monitors on Ubuntu 10.04 Gnome.  I installed the card and booted the live cd.  Both monitors are recognized when I go to the display settings, but when I un-check the mirror box, nothing changes.  I am still only getting one monitor.  I was previously using 9.10 and it sometimes worked, but not always.  Any thoughts?  Thanks.

---

### Post by dino99 on 2010-05-04
sudo aticonfig --initial

[http://www.h3manth.com/content/fixed-enabling-desktop-effects-ati-ubuntu-lucid](http://www.h3manth.com/content/fixed-enabling-desktop-effects-ati-ubuntu-lucid)

---

### Post by whatch on 2010-05-04
When I try:  sudo aticonfig --initial with the live cd I get "sudo: aticonfig: command not found"

---

### Post by Mark Phelps on 2010-05-04
Doesn't matter because when you reboot, you will lose all the changes.  Changes made while in LiveCD mode do not persist across reboots.

---

### Post by Squarc on 2010-05-15
Hey,

I have this same problem in KDE too. aticonfig doesnt seem to exist on my pc, and neither does it exist int he repositories (tried all except for lucid-backports)...
But it gets wierder: I dont have a /etc/X11/xorg.conf file. nor any xorg.conf.backup or something alike...
I've never worked with the ATI driver before, can someone with ATI experience please tell me what to do to get dualscreenworking?

Thanks,
Squarc

---

### Post by Zoharc on 2010-07-27
I have dual screen/clone screen set up on Ubuntu 10.04 on ATI Radeon X1250

I have simply used the System Monitors tools to set my displays. However, it is important to note that said tool was entirely unresponsive until I have removed any additional appearance effects. After-which, a simple reboot allowed me to use Clone displayed with Compiz, or big desktop without Compiz. 

Hope that helps you.

---

