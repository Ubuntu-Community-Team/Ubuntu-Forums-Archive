---
title: "no ati H/W acceleration in x.org"
date: 2005-02-21
forum: General Help
---

### Post by I_NEED_HELP on 2005-02-21
I have just upgraded to the hoary hedgehog release to try getting hardware acceleration to work as i believe my ati igp340m chip is not supported with xfree.  

After installing i removed old xfree drivers and installed x.org drivers i then followed the ati setup guide in the howto sevtion.  however i still have mesa acceleration.  

Please help what have i missed.  does x.org still use the xf86Config-4 file or does it use something else.

[edit]
From what i gather i xorg uses an xorg.conf file in /etc/x11 however this does not exist on my system.  Am i right and if i am how do icreate an xorg.conf file.

---

### Post by Jezze on 2005-02-22
x.org uses the /etc/X11/xorg.conf file... you have most likely not installed all the neccessary packages if that file is missing....

---

