---
title: "Help needed on ATi Drivers"
date: 2006-04-11
forum: General Help
---

### Post by nolongerlivecd on 2006-04-11
I just installed Ubuntu 5.10 on my laptop with ATi Mobility Radeon X700, and I cannnot connect to my network. As such, I can't apt-get the fglrx drivers. Is there any other way I can do so? What configuration should I use?

---

### Post by Numeri on 2006-04-13
Well... I'm new to linux but here's my rant:

Try changing the xorg.conf's driver configuration
I recommend making a backup from your xorg.conf first:
[PHP]$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup[/PHP]
Then editing the xorg.conf:
[PHP]$sudo nano /etc/X11/xorg.conf[/PHP]
(or sudoedit or sudo view or sudo vim)

In xorg.conf under Section: "Device" change the Driver to Driver: 'vesa'
using the basic vesa driver should get you into gnome from where you can get your network/internet working and use apt-get to update/install your drivers. 

I myself have a ATI Xpress 200M but I haven't been able to get the fglrx running.

Hopes this helps.

---

