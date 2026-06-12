---
title: "usb keyboard/mouse won't work"
date: 2009-10-04
forum: General Help
---

### Post by lestatius on 2009-10-04
I just did a fresh installation of ubuntu and now my keyboard(g15) and my mouse(g5) won't work(when I enter the bios my keyboard does work). Meaning I can't type in my login info at the login screen. Before I had dual boot windows/ubuntu and it worked fine. But I was having some problems with grubloader and startup so I decided to delete all partitions on my hard discs using gparted and do a fresh ubuntu reinstall but now I can't figure out a solution for this. I don't have a ps/2 keyboard/mouse. Some help would be appreciate.

and one last question. what's the best way to manage the mbr when running dual boot? thanks in advance.

---

### Post by DenysT on 2009-10-04
While in the bios settings look for a setting for enable USB legacy devices. Turning this option off can cause the USB keyboard and mouse to not be recognized after the bios turns over the computer to the boot loader.

---

### Post by lestatius on 2009-10-11
I tried that but didnt work. I did a full reinstall and just running vmware server now. That will do for now. thanks anways :)

---

