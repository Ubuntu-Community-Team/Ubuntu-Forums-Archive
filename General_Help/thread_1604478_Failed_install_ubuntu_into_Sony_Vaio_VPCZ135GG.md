---
title: "Failed install ubuntu into Sony Vaio VPCZ135GG"
date: 2010-10-24
forum: General Help
---

### Post by jackyng722@gmail.com on 2010-10-24
Hi, this is my first time trying to install Ubuntu. I actually got this new notebook to install ubuntu - I just can't stand Windows. Here's my config,
 
Sony VPCZ135GG
Intel Core i5-580M
4G memory 
NVIDIA 330M Graphics
 
My trial steps as below according to instructions.
 
1. I downloaded from the official site ubuntu 10.10 desktop version (32 bit). 
2. Flashed it onto a USB drive
3. Restarted computer
4. Boot into USB drive
 
Then the problems starts to occur. First I notice that the screen becomes pink (instead of the normal brown / orange) and the fonts are barely readable, but I can still make out the icons for "try ubuntu" and "install ubuntu". Seems like it's an obvious driver problem. I try to go on with the "install ubuntu" option even the screen is abnormal thinking that there might be possible ways to fix this after install and update. Installation finishes. I try to reboot and it just stalls with the screen blank and the CPU running hot.
 
Pls help! I really can't stand windows!!!!!
 
Thanks in advance!

---

### Post by P4man on 2010-10-24
First of all, next time you buy a laptop specifically for ubuntu, Id strongly recommend you do a bit of research first, and buy one that is known to support ubuntu (system76 or similar if thats an option).

Anyway, your laptop seems to have "Optimus" dual graphics (intel GPU and nvidia) which isnt supported on linux yet, at least not the way its meant to be used. Does your bios have an option to set the videocard by default to intel or nvidia?

If not, try nomodeset. When you boot the machine, right after the bios logo, when you see the purple screen with keyboard logo at the bottom, press any key. You should get a menu. Then in f6 menu, select nomodeset. Then "try ubuntu".

If that solves it, then be adviced that after installation you will need to edit grub to apply the nomodeset flag again, but Ill explain that if it actually helps.

---

