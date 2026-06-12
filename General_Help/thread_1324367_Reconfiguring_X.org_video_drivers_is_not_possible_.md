---
title: "Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid."
date: 2009-11-12
forum: General Help
---

### Post by blackmajik2021 on 2009-11-12
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.

I get this error when trying to install the hardware drivers for my video card. I tried to do it manually first,and I think thats why everything is messed up. I've tried using 

sudo dpkg-reconfigure xserver-xorg

but that did not fix it either. help! :[

---

### Post by Giblet5 on 2009-11-12
Remove it and restart the X server ```
sudo rm -f /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

Now you're back to square one. No driver. No wrong config.

What driver do you use?

---

### Post by Digikid on 2009-11-20
I did this and it STILL hapenes exactly the same.

---

### Post by burdebc on 2010-12-02
I tried this and it worked fine,  I was able to reactivate the proprietary driver, and it began working perfectly.

---

### Post by vanquishedangel on 2011-02-19
> **Giblet5 said:**
> Remove it and restart the X server ```
sudo rm -f /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

Now you're back to square one. No driver. No wrong config.

What driver do you use?

Well I use ati 4350 card, not sure of the driver. I was using the one ati had on their site but I cleaned my computer with gtk orphan and it deleted fgrlx, but nothing else, like the control center was still there and other files so i got the error here when trying to re-install the driver. Any way, your directions worked except the screen went black and when i rebooted i booted to the default wallpaper of maverick, and nothing else, no mouse no nothing, so i booted into safe mode by holding shift as my comp booted and choose graphics safe mode then installed the driver from there. I installed the one from jockey because the website one no longer seems to work for me now.

---

### Post by maff on 2012-01-13
> **blackmajik2021 said:**
> Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.

I get this error when trying to install the hardware drivers for my video card. I tried to do it manually first,and I think thats why everything is messed up. I've tried using 

sudo dpkg-reconfigure xserver-xorg

but that did not fix it either. help! :[

Know this is an old thread, but it was top of the google search when i looked up this problem so thought it might help other google searchers if i posted my solution.

Removed a broken symlink for 
fglrx_drv_video.so

from
/usr/lib/dri

and it all started working again.

---

