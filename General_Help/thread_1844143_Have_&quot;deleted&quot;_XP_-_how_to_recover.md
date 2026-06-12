---
title: "Have &quot;deleted&quot; XP - how to recover?"
date: 2011-09-14
forum: General Help
---

### Post by zozza on 2011-09-14
Hello,

I have made a silly mistake which I hope is recoverable. 

I had Ubuntu and XP installed but when I tried to boot into XP just now I  got the option of restoring the filesystem.  I accidentally pressed OK  and it started to operate.  After a few seconds I rebooted the computer  to stop it.

I now find that when I access the XP partition in gnome-terminal on /dev/sda1 through /media/nameofXPdrive it shows this:

ls: cannot access boot.ini: No such file or directory
ls: cannot access CONFIG.SYS: No such file or directory
ls: cannot access Intel: No such file or directory
ls: cannot access IO.SYS: No such file or directory
ls: cannot access MSDOS.SYS: No such file or directory
ls: cannot access NTDETECT.COM: No such file or directory
ls: cannot access ntldr: No such file or directory
ls: cannot access pagefile.sys: No such file or directory
ls: cannot access Program Files: No such file or directory
ls: cannot access RECYCLER: No such file or directory
ls: cannot access RHDSetup.log: No such file or directory
ls: cannot access sysprep: No such file or directory
ls: cannot access WINDOWS: No such file or directory

There are various files in WINDOWS which I would like to keep.  

There were also other directories that exist(ed) which are not listed above.

There is 12GB free so I know the files have not totally disappeared  because the drive is 90GB.  The "disk utility" shows a 90GB NTFS drive.   GParted also shows 90GB and it shows /dev/sda1 having a "boot" flag.

What can I do to get back the directories and files?

Thanks

---

### Post by LowSky on 2011-09-14
What version of Ubuntu are you using? Have you enable NTFS support so you can read the drive from Ubuntu's file system.

I'm not sure exactly you tried to do, but when you reboot in the middle of process that involves repairing your system's hard drive, batty things can happen.

---

### Post by Basher101 on 2011-09-14
One thing i learned the HARD way (like you), NEVER EVER EVER (!) stop disk operations through a forced shutdown. Looks like your XP is busted, you should try to copy over all important files you can still find and make a reinstall of windows. This should be your final option, if there is no hope in other words, just read suggestions of other users before you attend this. Maybe they can help you to restore something.

---

### Post by zozza on 2011-09-14
> **LowSky said:**
> What version of Ubuntu are you using? Have you enable NTFS support so you can read the drive from Ubuntu's file system.

I'm not sure exactly you tried to do, but when you reboot in the middle of process that involves repairing your system's hard drive, batty things can happen.

I am using 10.04 LTS.

---

### Post by Habitual on 2011-09-14
> **Basher101 said:**
> ...NEVER EVER EVER (!) stop disk operations through a forced shutdown

+1
or during apt-get update

XP is probably Toast.
Files may be recovered if the partition for XP can be accessed.

Terminal >
```
sudo fdisk -l
```
and post output here.

---

### Post by zozza on 2011-09-15
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10812    86847358+   7  HPFS/NTFS
/dev/sda2           10813       18813    64267265    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3           18814       19451     5124735    c  W95 FAT32 (LBA)
/dev/sda4           19452       19457       48195   ef  EFI (FAT-12/16/32)
/dev/sda5           10813       17598    54501376   83  Linux
/dev/sda6           17598       18813     9764864   82  Linux swap / Solaris

---

