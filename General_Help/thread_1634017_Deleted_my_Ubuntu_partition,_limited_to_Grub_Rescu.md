---
title: "Deleted my Ubuntu partition, limited to Grub Rescue"
date: 2010-11-29
forum: General Help
---

### Post by trhoresh on 2010-11-29
So, I was dual-booting Ubuntu and WinXP on my netbook, but decided I wanted to go back to Windows only. I deleted the Ubuntu partition using GParted without thinking about the bootloader issue. Now, when I start-up my computer I get to Grub Rescue and that is it. 
 
Should I just follow the instructions listed under the other thread "stuck at grub rescue" or is there something special I have to do in my case?
 
Thanks,
 
-Travis

---

### Post by oldfred on 2010-11-29
You need to reinstall a windows or windows like boot loader to the MBR.

For XP the command is fixMBR. 

OR from a Ubuntu or just about any linux rescue type liveCD install just lilo to the MBR. Lilo works like windows in booting & jumping to the PBR partition boot sector.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by holycow131415 on 2010-11-29
Easiest way is to prob boot off your windows cd and do a repair

---

### Post by trhoresh on 2010-11-30
Problem solved
 
Boot booster was enabled, so F2 is what I needed to be pressing, not ESC. Got that switched around and booted from CD to my Asus Recovery Disk. 
 
Thanks for the input guys!

---

