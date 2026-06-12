---
title: "Ubuntu Crashes on boot screen, and when i edit the grub stuff i get no x server"
date: 2010-09-27
forum: General Help
---

### Post by l32007 on 2010-09-27
PLEASE LOCK

Hi, thanks for your time.
When i start up ubuntu it gets stuck on the splash screen. I can press the off button on my computer, it will show the turning off splash screen.

If i remove quiet splash. i end up with no X server and only a console.

Can somebody help me?
:(


Running on an F3 Series asus laptop
8600M Gts 
2.2ghz Core 2

Thanks,
L32007

---

### Post by l32007 on 2010-09-27
when i type
StartX into the console (after root login)
It says error parsing xorg.conf.
So im thinking can somebody send me a failsafe / default version of xorg.conf
Update: i recently added no logo to xorg.conf and i'm removing it to see the results.

---

### Post by l32007 on 2010-09-27
Alright, its fixed. It looks like configuring the xorg must be done perfectly or you'll end up in the situation where i was in
So, please lock and keep for noob reference

If you edit xorg.conf and cant boot
open grub, press E and remove "quiet splash"
login to terminal
Type
sudo nano /etc/X11/xorg.conf
Remove the edits
press Ctrl + X
and Y
then restart.

Sorry for wasting time talking to myself lol.

l32007

---

