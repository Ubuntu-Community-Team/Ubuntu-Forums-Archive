---
title: "Cannot switch back to Windows Vista?"
date: 2011-03-08
forum: General Help
---

### Post by tonamon on 2011-03-08
Man..I cannot press F8 to go into safe mode like Vista could. I cannot see Windows Vista on the boot loader thing (Grub I believe?) and i don't know how to switch back from linux because i wanna play my APB and other stuff.....i updated grub and this is what showed.```
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```
Please help, i really don't want linux any more...

---

### Post by YesWeCan on 2011-03-08
No problem.
A few more details about your system are needed.
Would you post the output of 'sudo fdisk -l'?

It may be you have accidentally messed up your Vista bootloader and you will need to use your Vista CD (if you have it) to repair it.

---

### Post by tonamon on 2011-03-08
This is what i got```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b3384

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76699   616077312   83  Linux
/dev/sda2           76699       77826     9052161    5  Extended
/dev/sda5           76699       77826     9052160   82  Linux swap / Solaris

```

---

### Post by YesWeCan on 2011-03-08
I am afraid there is no Vista showing on this drive.
When you installed Ubuntu did you opt for using the whole drive?

---

### Post by tonamon on 2011-03-08
No... i selected "Duel Boot" or something like that. I made the 600gb not equal linux had like 550gb and vista was left with the lowest (or at least near the lowest)

---

### Post by YesWeCan on 2011-03-08
Dual boot is what you wanted. The installer has used the whole disk for Ubuntu.

---

### Post by tonamon on 2011-03-08
So can you tell me how to go back to vista?

---

### Post by YesWeCan on 2011-03-08
No. :(

---

### Post by tonamon on 2011-03-08
Ah, i was wondering, i have a windows 7 disk. Can i use that to install? Or will it be a waste?

---

### Post by YesWeCan on 2011-03-08
Personally, I use both Windows 7 and Ubuntu. Windows 7 is much better than Vista, in my experience. It seems fast and stable. Linux is faster and stable but there is a big difference in application support and the user interface. Windows is easier and holds your hand more whereas Ubuntu allows you to do more interesting things if you are happy to roll your sleeves up.

---

### Post by 3rdalbum on 2011-03-08
Just restore Windows from your backup. If you don't have a backup, remember: Before doing ANY partitioning operation, MAKE A BACKUP. Partition resizing is a hack; it's really amazing that it works as often as it does.

---

### Post by Frogs Hair on 2011-03-08
I dual boot as well and went from XP to 7 and and missed the V word  all together . For home use that is .

---

### Post by Quackers on 2011-03-08
Did you make a set of recovery dvd's when you got the computer? Without those it would appear that Vista is toast.

---

### Post by tonamon on 2011-03-09
NOOOOOOOOOOOOOOOOOO, I do have Windows 7 CD however, i was trying to run the setup for 64 and this is what showed up```
wine /media/US-HP/Win7OS64/setup.exe
Trying to load PE image for unsupported architecture (AMD-64)
err:process:create_process starting 64-bit process L"D:\\media\\US-HP\\Win7OS64\\setup.exe" not supported on this environment
wine: Bad EXE format for D:\media\US-HP\Win7OS64\setup.exe

```
Also, I was able to restore my Vista several times before using F8 to go into system recovery.

---

### Post by tonamon on 2011-03-09
bump

---

