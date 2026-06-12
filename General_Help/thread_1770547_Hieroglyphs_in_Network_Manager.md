---
title: "Hieroglyphs in Network Manager?"
date: 2011-05-29
forum: General Help
---

### Post by MoebusNet on 2011-05-29
This is a new one on me:

If there is no wireless signal when I boot up my notebook, when I check Network Manager's list of available wireless networks there are about 5 networks listed. The listed names are in some font like hieroglyphs or wingdings or something, The thing is, I'm way out in the country with no neighbors with wireless routers. The only wireless router around is when I enable my cellphone's wireless router capability; it is usually off.

This is kinda strange; does anyone have any ideas as to what is going on? I appreciate any insight.

---

### Post by linuxinstalledfromhdd on 2011-05-29
have you booted from either a live usb stick of Ubuntu or live bootable disc of Ubuntu to see if this problem goes away?

---

### Post by MoebusNet on 2011-05-29
> **linuxinstalledfromhdd said:**
> have you booted from either a live usb stick of Ubuntu or live bootable disc of Ubuntu to see if this problem goes away?

Hmmm; no I'll have to try that. Thanks!

---

### Post by linuxinstalledfromhdd on 2011-05-29
I want to see if it is a hardware issue or a OS issue.  If you have the same thing happening on a freshly installed disc of Ubuntu, and an older disc, my guess is it might be hardware related.  Hopefully you have some cd-rs or dvd-rs to burn too..

---

### Post by MoebusNet on 2011-05-29
OK, sorry to take so long (Ubuntu Lucid Lynx really doesn't want to run as a Live-CD on my notebook).

The strange wireless networks don't show up in Maverick Meerkat Live-CD, Puppy Linux (Lucid & Wary) or Lubuntu 11.04 Live-USB.

This leads me to believe that it is not the hardware. The only thing I can think of is that this began to occur after an unsuccessful attempt to set up an ad-hoc network. It didn't work, so I deleted the new wireless network.

Would reinstalling network manager be indicated?

EDIT: I tried to take a screenshot of the Network Manager menu showing the strange wireless networks, but attempting to take the screenshot closes the Network Manager drop-down menu.

---

### Post by MoebusNet on 2011-05-30
I've got this one fixed; I right-clicked on Network Manager's icon in the upper taskbar, left-clicked on "Edit Connections", and deleted all of the remembered networks. After cold-booting my computer the next morning with  no wireless routers near, the list of wireless networks nearby is empty (as it should be).

---

