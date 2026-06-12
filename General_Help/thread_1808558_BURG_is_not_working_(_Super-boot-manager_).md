---
title: "BURG is not working ( Super-boot-manager )"
date: 2011-07-20
forum: General Help
---

### Post by Skopuningurin on 2011-07-20
Hi

I installed Super-Boot-Manager a few days ago. When it was installed, I installed BURG manager, chose a screen and restarted... aaannnd.. Nothing happened at all. The same old Grub screen came as always. I am dual booting with Windows Vista.
Anyone know a solution to this problem?

Running Ubuntu 10.04, on a Acer Aspire 6930G

---

### Post by dcstar on 2011-07-21
> **Skopuningurin said:**
> Hi

I installed Super-Boot-Manager a few days ago. When it was installed, I installed BURG manager, chose a screen and restarted... aaannnd.. Nothing happened at all. The same old Grub screen came as always. I am dual booting with Windows Vista.
Anyone know a solution to this problem?

Running Ubuntu 10.04, on a Acer Aspire 6930G

```
sudo dpkg-reconfigure burg-pc
```

---

### Post by Skopuningurin on 2011-07-22
... Nevermind, I'm just as lost.

---

### Post by jRdbRR on 2011-07-27
sorry meant my og comment for somewhere else

but this isnt working for me either, even using that command listed above

---

### Post by coldraven on 2011-07-27
Open a terminal with Ctrl+Alt+T
Type ```
sudo update-burg
```During the Burg install you have to select which drive it will go on. You have  to press the Space bar to select which one, in my case it is dev/sda.
To find out do ```
sudo fdisk -l
```You will see something like this ```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17929   144006521+  83  Linux
/dev/sda2           17929       30402   100190209    5  Extended
/dev/sda5           29165       30402     9936896   82  Linux swap / Solaris
/dev/sda6           17929       28659    86191104   83  Linux
/dev/sda7           28659       29164     4059136   82  Linux swap / Solaris
```This means that "sda" is my only drive and "sda1" is the first partition and the "*" (asterisk) means that it is bootable. Maybe you should find out this info first!

You can change the  options, themes etc. at boot-time or do this to save yourself from re-booting just to see the result.
```
sudo burg-emu
```
I hope that this helps :D

---

### Post by Skopuningurin on 2011-07-27
This is what I got when I did " fdisk -f "
"   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567       31184   237899776    7  HPFS/NTFS
/dev/sda3           31184       60347   234251264    7  HPFS/NTFS
/dev/sda4           60347       60802     3650560   12  Compaq diagnostics

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e31ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59685   479417344   83  Linux
/dev/sdb2           59685       60802     8967169    5  Extended
/dev/sdb5           59685       60802     8967168   82  Linux swap / Solaris
"

I suspect that I may have ****** something up while installing Super Boot Manager. When I open it and enters " burg manager ", on the first page, I can choose which hdd/partition to in stall it. But I can only chose " sdb " while I think it should be " sda "... I dunno. I'm a noob, as you can see. :'(

---

### Post by coldraven on 2011-07-29
I'm not an expert but I think that "sdb" is probably correct. That's because the MBR which was originally created by Windows is sitting on "sda". Don't mess with that!
I think how it works is like this:
The MBR was altered by Ubuntu so that you can dual boot. 
If I'm correct it only made a tiny change because the MBR has only very little space. But it puts a pointer to where the GRUB files are. In your case on sdb we think. So then when GRUB pops up if you select Windows it will point back to /dev/sda2 and boot from there. (Drive C: in Windows)
If you select Ubuntu it will point at sdb. Why it does not show an asterisk in your results I don't know.
Hopefully someone else will give some advice. Good luck :)

MBR is the Master Boot Record
My first post said fdisk -l (lowercase L) not -f (I don't know what that does)

---

