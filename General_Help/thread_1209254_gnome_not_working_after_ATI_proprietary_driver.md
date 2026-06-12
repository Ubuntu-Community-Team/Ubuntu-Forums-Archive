---
title: "gnome not working after ATI proprietary driver"
date: 2009-07-10
forum: General Help
---

### Post by gralco on 2009-07-10
Hi, I have a ATI Radeon HD 4890 and when I installed the proprietary driver and restarted my machine gnome didn't start correctly, please help.

---

### Post by Legace on 2009-07-10
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

