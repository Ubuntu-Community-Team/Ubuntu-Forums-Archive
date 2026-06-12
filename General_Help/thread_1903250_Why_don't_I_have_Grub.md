---
title: "Why don't I have Grub?"
date: 2012-01-02
forum: General Help
---

### Post by birdfoot on 2012-01-02
Could anyone let me know what information might be pertinent in determining why I don't see Grub when I bootup?

Lubuntu 11.10 32 bit
Old, very large Viewsonic monitor 
Only one OS: Lubuntu

---

### Post by arpanaut on 2012-01-02
On a single OS install the Grub Menu does not show by default.
If you need the options of that menu;  after Post start tapping the shift key and the menu will appear.

---

### Post by lukeiamyourfather on 2012-01-02
By default GRUB is hidden. If you haven't manually changed that then the menu won't show up during booting.

---

### Post by QIII on 2012-01-02
You will see GRUB if you do an update that installs a new kernel version.  At that point you will be offered the opportunity to select between the two.  

I'm on my mobile right now so I can't give you a link, but you can change the default GRUB behavior, particularly time-out, so that you will see the grub menu.

Edit:  Looks like ds305 updated this in September, so it should be up to date.  Look for "time-out" or "time out".

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by MartijnNL on 2012-01-02
> **QIII said:**
> You will see GRUB if you do an update that installs a new kernel version.

As far as I know this only happens if you have different OS's, not different kernel versions. I have plenty of kernel versions installed, but no GRUB menu on boot, unless I press and hold shift after the POST like arpanaut says.

---

