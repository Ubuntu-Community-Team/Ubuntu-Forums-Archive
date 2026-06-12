---
title: "Upgraded graphics card now no Ubuntu, just XP"
date: 2011-06-06
forum: General Help
---

### Post by Amused2Death on 2011-06-06
Sad but true, i upgraded from an Nvidia 7600gt to a gtx560 now Natty wont load but XP cruised through the upgrade.

I have tried safe mode and graphics fix but it takes me back to normal boot and this is where i get lost.

I have to login via this screen then having done so it obviously is waiting for me to type some more. Trouble is its like terminal and i have no idea what to type to get it to try and load Natty.

So would someone mind telling me what to type to get it to load the gui or how to fix a broken graphics upgrade.

thanx in advance

---

### Post by mastablasta on 2011-06-06
if you had proprietary drivers installed before then you need to remove them first (same procedure as ini windows) then reboot and install new ones.

---

### Post by Amused2Death on 2011-06-06
Bugger,
so its back with the old card (sadness thats a lot of work) and remove drivers (double sadness).

Just how does one remove drivers in Ubuntu please.

---

### Post by mastablasta on 2011-06-06
if you had proprietary drivers you need to remove them (usually they are then replaced by opensource drivers) if not then there is something else. but i am not familiar with nvidia card and their issues.

---

### Post by Amused2Death on 2011-06-07
Ok i followed these instructions from Cappy in 2007 (forum search)

BUT i didnt use the last line. I shut down, replaced the graphics card with the new one, chose safe mode with graphics upon reboot and did driver update and all is good with the world once more.

Thanx

[I]Here's what I use for my Feisty:

Code:
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`[/I]

---

