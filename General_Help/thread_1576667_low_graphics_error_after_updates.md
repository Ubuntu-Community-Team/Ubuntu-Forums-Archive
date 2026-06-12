---
title: "low graphics error after updates"
date: 2010-09-17
forum: General Help
---

### Post by jason82 on 2010-09-17
I installed updates on ubuntu 10.04 and when i reboot i get an error that states some thing about low graphics mode.. ill post a better explanation later but it stops there i cant even move the mouse, or use the keyboard to hit ok... any help ?

---

### Post by Rubi1200 on 2010-09-18
Have you tried editing the GRUB menu using the nomodeset option?

Does the problem persist with an older kernel version?

---

### Post by jason82 on 2010-09-18
i dont have older kernels in my grub menu and dont know about nomodest...      ugh i know im still a noob at this

---

### Post by Rubi1200 on 2010-09-18
As the computer is booting hold Shift to bring up the GRUB menu (assumes you only have Ubuntu) then highlight the Ubuntu entry and press "e" to edit.

Find the line that ends with```
 ro quiet splash
```
Remove quiet splash and type nomodeset.

Then "Ctrl" + "x" to boot.

If that makes a difference then we can talk about a more permanent solution.

---

### Post by jason82 on 2010-09-18
ok i tried that when i press ctrl x nothing happens but if i go back and press b to boot it just reboots back to the grub menu

---

### Post by jason82 on 2010-09-20
:confused::confused::confused::confused::confused:

---

### Post by r2rX on 2010-09-20
Question, are you using an ATi or nVidia display adapter? And if so, are you using proprietary drivers?

Cause i've had a similar issue, with both ATi and nVidia, after installing updates (especially related to Kernel updates) where if you have updated and rebooted, the display drivers don't respond properly...thus, low graphic mode.

If the above scenario is the case, simply uninstall your display drivers and re-install them. Also, once reinstalled, check your xorg.conf file to see if the entry for your display adapter is present and configured properly.

But concerning the keyboard and mouse....i'm not sure....you can try entering "recovery mode" (safe mode) and see what happens.

r2rX  :)

---

### Post by efflandt on 2010-09-20
Did you use System > Administration > Hardware Drivers to install your nvidia drivers or something else right from nVidia?  If you used Hardware Drivers everything should update automatically, but if you installed other drivers yourself, you may need to reinstall your video drivers after kernel updates because the new kernel may be missing headers for your video.

---

### Post by jason82 on 2010-09-21
its an nvidia card but i cant get past the warning message (no gui) to even begin to try reinstalling drivers unless there is a way to do it from a live cd maybe

---

### Post by jason82 on 2010-09-28
):P):P:confused::confused::confused::confused::confused:

---

