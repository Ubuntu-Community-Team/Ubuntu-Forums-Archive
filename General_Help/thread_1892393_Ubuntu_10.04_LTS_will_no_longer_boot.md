---
title: "Ubuntu 10.04 LTS will no longer boot"
date: 2011-12-07
forum: General Help
---

### Post by lordcirth on 2011-12-07
I dualbooted LTS on a Win7 rig, installed with no serious problems, been running about a week now.  I come home, boot to Win7 to get some files, reboot to Ubuntu.  It goes to GRUB (v2 I think) I choose Ubuntu, it starts loading.  When all the dots go red (just before login loads) it reboots back to BIOS, and keeps looping every time I choose Ubuntu!  I have no idea whats wrong, so far as I know all I installed since last boot was some winetricks dlls, and python.  If I boot recovery mode it boots terminal just fine, so maybe it's Gnome?  Terminal access should be enough to let me fix it, if someone can tell me what to do.

Gigabyte mobo
Phenom II X6 3.2Ghz
4GB x 2 DDR3 1333 RAM
Radeon 5830

Plz help, Im loving Ubuntu and I want it back.  ty.

---

### Post by bluexrider on 2011-12-07
if you have a live CD you can install and run boot-repair 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lordcirth on 2011-12-08
I think I found the problem.  Win7 is still showing full HDD size, apparently it doesn't recognize the EXT4 partition, and overwrote something.
Is there a way to fix this in Windows before restoring Ubuntu?  Otherwise it'll just happen again.

---

