---
title: "URGENT!!! - grub error :("
date: 2011-03-07
forum: General Help
---

### Post by liquidmonkey on 2011-03-07
hi,
i have win7 on one partition and ubuntu on the same partition but of course split.
my laptop is dual boot and it all works UNTIL....

i needed extra space for my win7 so i went into DISK MANAGER and deleted the ubuntu partition.
after i did i thought i just screwed up.
when i rebooted, it was confirmed :(

now i get
'error, grub rescue>'

have read a few threads but no one seems to have the same problem as me.
i do not have a recovery cd.


so now, i have ubuntu ready to install (from cd) onto my laptop but am not sure if i should.
there are 2 partitions.
1) sda1 ntfs (my win7)
2) sda2 fat32 (i am assuming this is where the grub is, so if i delete it, will my problems go away)

the only thin stopping me from deleting the fat32 partition is that it does say 'windows NT/2000/XP'.


so before i make a bigger mess, what do you think?
my goal is to get rid of the ubuntu partition and only have win7 left.
i'm using ubuntu in virtual box anyway :)

---

### Post by kiyop on 2011-03-07
The GRUB(2) boot loader was installed on MBR of your hard disk and refer to the /boot/grub directory of the ubuntu partition.
You have deleted the ubuntu partition, so GRUB(2) boot loader cannot access to the /boot/grub directory and cannot act correctly.

One way is to install the default MBR of Windows 7.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
bootrec /FixMbr

Alternatively, you can install lilo by the method shown below.

Boot with Ubuntu LiveCD

Open terminal by clicking
"Application" -> "Accessories" -> "Terminal"

Type the following [FONT=monospace]
[/FONT]```
sudo apt-get udpate
sudo apt-get install lilo[FONT=monospace]
[/FONT]sudo lilo -M /dev/sda mbr
```

---

### Post by alphaamanitin on 2011-03-07
SuderGrub can also repair/rebuild windows MBR.

AlphaA

---

### Post by YesWeCan on 2011-03-07
> **liquidmonkey said:**
> so before i make a bigger mess, what do you think?
my goal is to get rid of the ubuntu partition and only have win7 left.
i'm using ubuntu in virtual box anyway :)
It is a common thing because it is not obvious how Grub works.

Grub replaced your MBR (thus disabling bios booting of Windows) and it needs files inside the Ubuntu partition in order to do anything at all.
So to access Windows you need to reinstate the original MBR (which the lilo program will do).

Ubuntu will run better as a dual boot than as a virtual machine. Next time, you might want to add Ubuntu to the Windows bootloader rather than using Grub. When you install Ubuntu choose advanced installation and install grub in the partition boot sector. Then in Windows download EasyBCD (free) and this will find and add Ubuntu to your Windows bootloader. This way, if you delete or mess up Ubuntu you will still be able to boot into Windows.

---

### Post by liquidmonkey on 2011-03-08
THANK YOU soooooooooooooooo much for this help!
totally worked (i used the first post suggestions)!!

and yeah, ubuntu does work when in dual-boot but for my needs, running it a virutal box works awesome. besides, if i need to do anything else, i can just switch over to windows.
i really love this virtual box!!!

thanks again!

---

