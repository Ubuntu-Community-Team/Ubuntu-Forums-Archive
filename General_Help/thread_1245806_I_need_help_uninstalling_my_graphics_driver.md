---
title: "I need help uninstalling my graphics driver"
date: 2009-08-20
forum: General Help
---

### Post by thingy87654321 on 2009-08-20
whenever i install the graphics driver for my ibm thinkpad t42p (ati firegl t2 driver) it wont boot, it shows a distorted screen and nothing else, i booted into a live cd (btw i am using 9.10) but i cant for the life of me figure out how to access the installed packages on the harddrive through synaptic so i can remove them, how do i accomplish this task

---

### Post by P4man on 2009-08-21
dont boot the live cd, boot the recovery console (option in grub menu). then type:

```
sudo apt-get remove name_of_package
```

tip: you can press TAB key for autocomplete if you're not sure about the name of the package. Just type in the first few characters, then press tab.

---

### Post by matthewbpt on 2009-08-21
I'm afraid your card is one of the cards that ATI has discontinued support for, so it's only supported by the now legacy Catalyst 9.3 driver. This driver isn't compatible with Jaunty as it is not compatible with the newest Xserver version, you have to stick to the open source drivers for this card if you want to use Ubuntu Jaunty+. However development for them is looking good so it's quite possible you'll get 3D support in the near future with the open source driver.

---

### Post by matthewbpt on 2009-08-21
> **thingy87654321 said:**
> whenever i install the graphics driver for my ibm thinkpad t42p (ati firegl t2 driver) it wont boot, it shows a distorted screen and nothing else, i booted into a live cd (btw i am using 9.10) but i cant for the life of me figure out how to access the installed packages on the harddrive through synaptic so i can remove them, how do i accomplish this task
You need to select boot into recovery mode in the GRUB menu, this will get you to a command prompt mode, select to go to root shell and type the following
```
sudo apt-get remove --purge xorg-driver-fglrx
sudo dpkg-reconfigure -phigh xserver-xorg
```

It should be uninstalled now and set to use the open source driver when you restart.

---

### Post by thingy87654321 on 2009-08-21
thanks it worked, but why didnt the driver work in the first place

---

### Post by thingy87654321 on 2009-08-21
ohh,   	   #3
matthewbpt didnt read your first post, well that sucks, does that basically mean if i used a older version of ubuntu it would work, because i want to try out the catalyst software on linux, and would my ASUS P5VD2-VM SE motherboard support linux, it has a pentuim d 2.66ghz and 512 mb of ram (only 384 usable because it shares the memory with the onboard graphics apadter

---

