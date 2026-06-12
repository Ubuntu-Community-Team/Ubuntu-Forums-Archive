---
title: "GRUB Help Please!"
date: 2011-01-14
forum: General Help
---

### Post by Jabrick on 2011-01-14
I just received a service pack update for Windows 7, and now when I boot Windows 7, it continuously restarts telling me its for the update. Is it possible that I have two boot loaders in the MBR? And if i do how can i delete the bootloader for windows 7?

Help is greatly appreciated.

---

### Post by garvinrick4 on 2011-01-14
#You never really have to delete a bootloader you can install a new one and it overwrites
the old one. No big deal really.
#Sounds like a Windows thing if you just installed updates to Windows.
#Takes a Ubuntu CD to reinstall grub2 to mbr if you cannot boot into it.
#Below is a few links if you believe it is bootmanager problem
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Jabrick on 2011-01-14
I believe I'm running Grub Legacy.
By the way if it helps when i boot Windows 7 from hd(1,1) windows begins to boot normally. But If i boot Windows 7 from hd(0,0) A greyish screen with some design pops up, and then restarts.

---

### Post by wilee-nilee on 2011-01-14
> **Jabrick said:**
> I believe I'm running Grub Legacy.
By the way if it helps when i boot Windows 7 from hd(1,1) windows begins to boot normally. But If i boot Windows 7 from hd(0,0) A greyish screen with some design pops up, and then restarts.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us more information, but it sounds like a windows problem, but lets see with this script.

---

### Post by boarder428 on 2011-01-14
If your running any Ubuntu version newer that 9.10 than it would install grub 2 by default.  If you installed Windows 7 then ubuntu I beleive by default it would install to (hd 0,1)
here is a copy of my boot entry for grub 2 for the windows partition only
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set dcd4c811d4c7ebb8
	chainloader +1
}

```
the question to ask is, can you successfully boot into Ubuntu with no problems?

---

