---
title: "quad monitors in ubuntu 10.10"
date: 2011-04-23
forum: General Help
---

### Post by black dawg on 2011-04-23
Hello everyone.

I am just coming back to ubuntu after a brief return to the darkside.  :)  I'm not a total linux newb but I know I still have alot to learn. I am having trouble getting my computer to display on my 4 monitors properly. I am running dual radeon hd 5750's.  I am trying to have a virtual screen 3840 x 2160 however it is making two virtual screens at 3840 x 1080.  I have the proprietary ati/amd drivers installed and catalyst control center.  Catalyst control center shows all 4 monitors but will only let me pair the monitors that are running off of the same card.  Any help would be greatly appreciated.  I am attaching my xorg.conf as well.  I figured it has to be something that I need to edit in there.  Thanks in advance!

---

### Post by dino99 on 2011-04-23
actual kernel(s) directly deal with X, so custom xorg.conf conflict, rename yours to boot without xorg.conf to know what happen then with/without control settings

AMD/ATI forum may help too
you can try with the latest packages from : xorg-edgers ppa

---

