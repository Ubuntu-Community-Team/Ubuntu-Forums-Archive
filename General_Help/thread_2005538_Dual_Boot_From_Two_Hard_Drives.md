---
title: "Dual Boot From Two Hard Drives"
date: 2012-06-17
forum: General Help
---

### Post by shibby4555 on 2012-06-17
So title says it all. Trying to configure grub to boot two operating systems. I've been reading about chainloading with grub. But grub is a tool that is above and beyond me.  I just keep finding myself pulling out my hair. I really am determined to accomplish this however. So any help would be greatly appreciated. I'm going for a drink to think about this one. Fdisk is below if it helps. Thank you for your input.

```
Disk /dev/sda: 1000.2 GB, 1000200658432 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953516911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2eff3493

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953516910   976758455   ee  GPT

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2f57

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1250260991   625129472    7  HPFS/NTFS/exFAT

Disk /dev/mapper/cryptswap1: 10.2 GB, 10200000512 bytes
255 heads, 63 sectors/track, 1240 cylinders, total 19921876 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17b5e116

```

---

### Post by drs305 on 2012-06-17
Unfortunately that doesn't give us enough information to help. 

Normally running "sudo update-grub" will find your OS's and add them to the Grub menu. If it doesn't, boot into your Ubuntu partition and install Boot Repair and try 'Recommended Repair'.

If that doesn't solve it, there is an option to run the boot info script. That will show us what you have and allow us to help.

Link to Boot Repair in my signature line.

---

### Post by shibby4555 on 2012-06-17
> **drs305 said:**
> Unfortunately that doesn't give us enough information to help. 

Normally running "sudo update-grub" will find your OS's and add them to the Grub menu. If it doesn't, boot into your Ubuntu partition and install Boot Repair and try 'Recommended Repair'.

If that doesn't solve it, there is an option to run the boot info script. That will show us what you have and allow us to help.

Link to Boot Repair in my signature line.

Wow certainly looks like it will do the trick, only problem is before I can apply any settings it says "Please install the [Parted] Packages. Then try again. No idea what dependency that could be. Your response is greatly appreciated.

---

### Post by shibby4555 on 2012-06-18
Bump.
[http://paste.ubuntu.com/1047796/](http://paste.ubuntu.com/1047796/)


So I'm trying to chain-load but the excellent tool provided above does not seem to want to cooperate with me.  The above link is the boot info. So I have a suspicion I could just append the following and be ok. But I never like arbitrarily adding code.

```

menuentry "Windows" {     insmod chain     insmod ntfs     set root=(hd1,1)     chainloader +1 } 
```

---

### Post by GreatDanton on 2012-06-18
You can buy box, in which you can place your HDD (I assume you have desktop computer). When you want to use one operating system remove the box, and when you want to use other OS place the box back into the computer.

It's not the solution to your problem, but only a workaround-maybe it will help you.

---

### Post by LostFarmer on 2012-06-18
The "Boot Info Script" indicates that you are missing the needed Vista/7 boot files 'boot manager'.  I do not have vista/7, but do a web search 'win 7 boot manager' will give needed info.

---

### Post by YannBuntu on 2012-06-19
Hello

> **shibby4555 said:**
> Bump.
[http://paste.ubuntu.com/1047796/](http://paste.ubuntu.com/1047796/)

Please run Boot-Repair from Boot-Repair-Disk or Ubuntu-Secure-Remix WITHOUT updating the software, then click "Recommended repair" and indicate the new URL that will appear.

---

