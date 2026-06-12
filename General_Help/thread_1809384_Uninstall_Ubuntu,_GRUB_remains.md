---
title: "Uninstall Ubuntu, GRUB remains"
date: 2011-07-21
forum: General Help
---

### Post by brettreardon123 on 2011-07-21
I was dual-booting Windows XP and Ubuntu, and Ubuntu stopped working so I decided to uninstall it. I used Windows Computer Management to format the Ubuntu drive, and rebooted to find that GRUB was still there with all the options (Ubuntu, Windows, etc). Since Ubuntu was broken, one of the primary reasons I wanted to format the drive was that I wanted to be able to boot straight into Windows without having to select anything in the boot process. Does anyone have an idea what I should do? Thanks in advance!

---

### Post by seawolf167 on 2011-07-21
Insert your Windows disc, boot off it, then select to enter the recovery console. Once there, type in the command shown below to overwrite Grub on the MBR with the Windows MBR

```
bootrec.exe /fixmbr
```

---

### Post by ahears on 2011-07-21
> **brettreardon123 said:**
> I was dual-booting Windows XP and Ubuntu, and Ubuntu stopped working so I decided to uninstall it. I used Windows Computer Management to format the Ubuntu drive, and rebooted to find that GRUB was still there with all the options (Ubuntu, Windows, etc). Since Ubuntu was broken, one of the primary reasons I wanted to format the drive was that I wanted to be able to boot straight into Windows without having to select anything in the boot process. Does anyone have an idea what I should do? Thanks in advance!


Windows 7 boot into recovery mode and try:

> 

[COLOR=Red] fixboot.exe c:\[/COLOR]



---

### Post by seawolf167 on 2011-07-21
> **ahears said:**
> Windows 7 boot into recovery mode and try:

in Windows 7 (and Vista) you have to call "bootrec.exe" first, in XP you don't, you can just issue the fixboot (to fix the ***partition boot record***) or fixmbr (to fix the ***mbr***). So using fixboot in this case would just recreate the Windows loader on that partitions boot record and leave the MBR (where GRUB resides) untouched.

---

### Post by drs305 on 2011-07-21
If you are currently on the Ubuntu LiveCD, you can restore the MBR from within Linux. Assuming the Windows boot files are intact and on your 'sda' drive, you can partially install the lilo bootloader to point the MBR back to your Windows installation:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Disregard messages after the second command and reboot. If the boot flag points to your Windows boot partition, this will likely allow Windows to boot.

---

### Post by mikejonesey on 2011-07-21
there is also a tool that you can use to restore windows mbr, i forget it's name think it's ms-mbr or somthing along those lines...

update: just google'd it, it's ms-sys, you can download from a few places in deb format...

---

