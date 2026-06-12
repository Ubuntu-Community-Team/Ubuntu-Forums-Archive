---
title: "GRUB not being changed - menu.lst not affecting bootloader"
date: 2010-04-18
forum: General Help
---

### Post by sab3156 on 2010-04-18
Hey, everyone.  I have a somewhat weird problem...

I am running Vista x64 and Ubuntu 9.10 x64 on a single partitioned drive.  

My bootloader shows:

2.6.31-20-generic kernel
2.6.31-20-generic (recovery)
2.6.31-14-generic
2.6.31-14-generic (recovery)
and two Vista partitions (/dev/sda1 and /dev/sda2, sda2 being a recovery partition).

Here is the relevant portion of my menu.lst:[INDENT][B]title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ffa8ff57-fead-4501-a17d-ec1453eca526
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ffa8ff57-fead-4501-a17d-ec1453eca526 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ffa8ff57-fead-4501-a17d-ec1453eca526
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ffa8ff57-fead-4501-a17d-ec1453eca526 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        ffa8ff57-fead-4501-a17d-ec1453eca526
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ffa8ff57-fead-4501-a17d-ec1453eca526 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        ffa8ff57-fead-4501-a17d-ec1453eca526
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ffa8ff57-fead-4501-a17d-ec1453eca526 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        ffa8ff57-fead-4501-a17d-ec1453eca526
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        ffa8ff57-fead-4501-a17d-ec1453eca526
kernel        /boot/memtest86+.bin[/B]

[/INDENT]The weird thing is that both the Vista partitions don't show up here in menu.lst, yet they are both displayed on the bootloader at system startup.

I installed another kernel (2.6.26.8-rt16), and added these lines to menu.lst:[INDENT]**title        Ubuntu 9.10, kernel 2.6.26.8-rt16**
** uuid        ffa8ff57-fead-4501-a17d-ec1453eca526**
** kernel        /boot/vmlinuz-2.6.26.8-rt16 root=UUID=ffa8ff57-fead-4501-a17d-ec1453eca526 ro quiet splash **
** initrd          /boot/initrd.img-2.6.26.8-rd16**

** title        Ubuntu 9.10, kernel 2.6.26.8-rt16 (recovery mode)**
** uuid        ffa8ff57-fead-4501-a17d-ec1453eca526**
** kernel        /boot/vmlinuz-2.6.26.8-rt16 root=UUID=ffa8ff57-fead-4501-a17d-ec1453eca526 ro  single**


[/INDENT]However, nothing changes in the bootloader at system startup... even if I comment everything out except this kernel's entry, everything remains the same...  so I can't boot this kernel.  :confused:

Anyone know what could be the problem?

Thanks for your time in advance.

---

### Post by oldos2er on 2010-04-18
Unless you upgraded from an earlier version of Ubuntu, 9.10 uses grub2, which no longer has menu.lst. See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by sab3156 on 2010-04-18
That's strange, because I see this when I do a **grub-install -v** :

[INDENT]**grub-install (GNU GRUB 0.97)**
[/INDENT]
So I'm using legacy.

---

### Post by ed-koala on 2010-04-18
Hmmm, perhaps if you ran boot info script and posted the results ...

How did you install 9.10?  Fresh or upgraded from an earlier version?  It's important to know.

---

### Post by john newbuntu on 2010-04-18
Perhaps there is something wrong with menu.list.   Did you run:
sudo update-grub

---

### Post by sab3156 on 2010-04-19
I installed 9.10 fresh after partitioning a hard drive that has Vista x64 on it.

I ran **update-grub**, but no luck.  :/

The most puzzling thing is:  why does the menu.lst file not reflect what is being displayed on the bootloader screen at startup?  I'm running legacy GRUB (version 0.97) so it should be using this menu.lst file...

I have attached the results of Boot Info Script to this post.

Thanks for helping out.

---

### Post by john newbuntu on 2010-04-19
As oldos2er mentioned, you have grub2 and not legacy grub per your results.txt output.  The menu.lst file in /dev/sda5 correspond to legacy grub.  Get the file menu.lst out of the way first since grub2 does not read it.  Grub2 goes against grub.cfg.

On skimming your grub.cfg, it appears to looks good. Do we still have a problem?

---

### Post by carl4926 on 2010-04-19
It's as simple as

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

---

### Post by sab3156 on 2010-04-19
Thanks.  With **grub-install /dev/sda **and **update-grub **I got the kernel I want to display on the bootloader... however, **grub-install -v** still says I am running GRUB 0.97 - how do I fix this?

Also, now my Vista partitions aren't showing on the bootloader at start-up.

This is what grub.conf says:

**### BEGIN /etc/grub.d/30_os-prober ###**
[B]menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7fd5575431e38b06
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8262f3fe62f3f4af
    chainloader +1
}[/B]

---

### Post by sab3156 on 2010-04-19
This is what it says when I'm running **update-grub** :


[INDENT] Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.26.8-rt16
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[/INDENT]Shouldn't this be updating boot/grub/grub.cfg and not menu.lst??  :confused:  And why isn't it detecting the Vista partitions?

---

### Post by sab3156 on 2010-04-19
Here is my **fdisk -l** :[INDENT][INDENT] Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x877d3b07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29904   240200700    7  HPFS/NTFS
/dev/sda2           37205       38913    13720576    7  HPFS/NTFS
/dev/sda3           29905       37204    58637250    5  Extended
/dev/sda5           29905       36901    56203371   83  Linux
/dev/sda6           36902       37204     2433816   82  Linux swap / Solaris

Partition table entries are not in disk order
[/INDENT]   
[/INDENT]Should the sda1 and sda2 have the same Id?

---

### Post by drs305 on 2010-04-19
When you boot, what version of Grub is displayed at the top of the menu. *That* is the version that is running.

You can try updating the Grub2 files by using the command specifically for G2. It shouldn't be necessary, but here it is:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

If you are still having problems, I would purge *grub* and then reinstall *grub-pc* and *grub-common*.

---

### Post by sab3156 on 2010-04-19
Thank you very much.  That actually detected the two Vista partitions this time:[INDENT][INDENT]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.26.8-rt16
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done


[/INDENT][/INDENT]However, it still does not show up like this on the screen... :/  I will try what you suggested, drs305, and get back to you.
[INDENT][/INDENT]

---

### Post by sab3156 on 2010-04-19
YES!  It worked after doing what you said - purging grub and reinstalling grub-pc and grub-common.  :D  Thanks!

---

### Post by MattParkins on 2010-10-25
Thank you DRS305, even though it should be unnecessary, your fix  fixed it for me!

:popcorn:

---

