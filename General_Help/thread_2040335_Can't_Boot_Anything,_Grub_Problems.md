---
title: "Can't Boot Anything, Grub Problems"
date: 2012-08-10
forum: General Help
---

### Post by khoraski on 2012-08-10
Could someone please help? 

I used to have Ubuntu 10.xx (don't remember exact version) as my main operating system, and then later, I decided to install Windows 8 CP to try it out.

I didn't get rid of Ubuntu, it's still on a partition. 

The problem is, after installing Windows 8 CP, it set itself up so it'd install as my main operating system and not boot into my grub anymore. Later, I wanted to boot back into Ubuntu, so I thought if I just used my LiveCD to update my grub, it would fix it. 

But now all it does it take me to a grub screen that is a command-line interface and tells me the grub version. It doesn't allow me to choose between operating systems to boot. 

And every time I try to update my grub now, I get an error.


So basically, now I can't boot into any of my operating systems and I'm only telling you this from my LiveCD.

I probably did something stupid and don't realize it, so I'd appreciate your help ASAP. This is my only computer, after all. :I

If you need any more information, just tell me and I'll provide it.

---

### Post by Shadius on 2012-08-10
You could try Boot-Repair. The link is in my signature. Windows likes to take over other bootloaders so that's why you weren't able to boot into Ubuntu after installing Windows. Also, maybe you can try holding down shift to see if the GRUB menu comes up? You can try that before using Boot-Repair. If that doesn't work, then use Boot-Repair.

---

### Post by khoraski on 2012-08-10
> **Shadius said:**
> You could try Boot-Repair. The link is in my signature. Windows likes to take over other bootloaders so that's why you weren't able to boot into Ubuntu after installing Windows. Also, maybe you can try holding down shift to see if the GRUB menu comes up? You can try that before using Boot-Repair. If that doesn't work, then use Boot-Repair.

Thanks, that kinda repaired my grub. 

I can boot into Ubuntu now, at least. But for some reason, the Windows 8 CP installation is not on that list. 

So I still can't boot back into Windows. If anyone knows how I could add that to the grub boot menu, that would be very helpful, since most of my stuff is on that. The partition Ubuntu is on is 9GB, while the partition Windows 8 is on is 114GB.

---

### Post by oldfred on 2012-08-10
Run this from a terminal:

sudo update-grub

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Shadius on 2012-08-10
> **khoraski said:**
> Thanks, that kinda repaired my grub. 

I can boot into Ubuntu now, at least. But for some reason, the Windows 8 CP installation is not on that list. 

So I still can't boot back into Windows. If anyone knows how I could add that to the grub boot menu, that would be very helpful, since most of my stuff is on that. The partition Ubuntu is on is 9GB, while the partition Windows 8 is on is 114GB.

Try
```
sudo update-grub
```
now and see if that updates the GRUB menu to add the Windows OS to it.

---

### Post by khoraski on 2012-08-10
> **Shadius said:**
> Try
```
sudo update-grub
```
now and see if that updates the GRUB menu to add the Windows OS to it.

Nope. It still doesn't put it on the list. It's installed to /sda3 if that is of any help.

---

### Post by Shadius on 2012-08-10
> **khoraski said:**
> Nope. It still doesn't put it on the list. It's installed to /sda3 if that is of any help.

Please post the output of:
```
sudo fdisk -l
```

---

### Post by khoraski on 2012-08-10
> **Shadius said:**
> Please post the output of:
```
sudo fdisk -l
```

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x381731e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1763    14155776   27  Unknown
/dev/sda2   *        1763        1776      102400    7  HPFS/NTFS
/dev/sda3            1776       15579   110879117+   7  HPFS/NTFS
/dev/sda4           15580       30402   119060052    5  Extended
/dev/sda5           15580       17516    15558921    7  HPFS/NTFS
/dev/sda6           17517       17990     3804148   83  Linux
/dev/sda7           17990       24344    51036868    7  HPFS/NTFS
/dev/sda8           29383       29871     3926016   82  Linux swap / Solaris
/dev/sda9           29872       30402     4252672   82  Linux swap / Solaris
/dev/sda10          24344       29170    38765568   83  Linux
/dev/sda11          29170       29382     1704960   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by Shadius on 2012-08-10
Also, you said you didn't remember what version of Ubuntu you have so let's find that out by using:
```
lsb_release -a
```
then
```
uname -a
```

---

### Post by khoraski on 2012-08-10
> **Shadius said:**
> Also, you said you didn't remember what version of Ubuntu you have so let's find that out by using:
```
lsb_release -a
```
then
```
uname -a
```

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid
```

```
Linux jason-laptop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux
```

Yea, 10.04. That was it.

---

### Post by Shadius on 2012-08-10
Now you said Ubuntu is on *sda3*? Could you post a screenshot from GParted? I'm trying to understand how you have your partitions set up. You have a lot!

---

### Post by khoraski on 2012-08-10
> **Shadius said:**
> Now you said Ubuntu is on *sda3*? Could you post a screenshot from GParted? I'm trying to understand how you have your partitions set up. You have a lot!

Sorry about that. I tend to play around with my computer a lot. I only made a couple partitions. I don't know where all the other ones came from.

[img]https://dl.dropbox.com/u/10434417/images/Screenshot.png[/img]

---

### Post by oldfred on 2012-08-10
Your main install is sda3, but sda2 is the boot partition as it has boot flag. Windows 7 normally creates a 100MB boot/repair partition to boot from, so 8 must do the same.

The warning in gparted says there is an issue with sda2 and you should click or right click on that and see what gparted says. If gparted cannot mount it, the the os-prober cannot mount it and see the boot files to add them to your menu.

You probably need to run chkdsk on sda2.

---

