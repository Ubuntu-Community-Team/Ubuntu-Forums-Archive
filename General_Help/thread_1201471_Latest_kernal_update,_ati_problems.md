---
title: "Latest kernal update, ati problems"
date: 2009-07-01
forum: General Help
---

### Post by Gorlist on 2009-07-01
Good day - last week? their was fairly large update for ubuntu, since then the latest kernel ( causes the desktop not to display correctly (black screen with pretty colours). 

I was running standard fglrx drivers through the "hardware drivers" panel.

The previous kernal remained working, but today I tried to fix the latest and ended up loosing both. If I go to recovery mode, and tell it to repair the xorg it made no difference. Ive even booted from livecd just to check and again xorg's are identical.

Ive also tried aticonfig --ini.... command.

What next?

ATI HD 4870
Ubuntu 9.04

This is on my business work station so critical :)

---

### Post by Legace on 2009-07-01
Reboot PC, select "Recovery mode" (you might need to press ESC) in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

### Post by Gorlist on 2009-07-03
Thanks Legace! worked great :)

---

### Post by Legace on 2009-07-03
> **Gorlist said:**
> Thanks Legace! worked great :)

No prob, enjoy ;)

---

