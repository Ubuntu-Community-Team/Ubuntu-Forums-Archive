---
title: "Remove Grub2 from /"
date: 2010-07-28
forum: General Help
---

### Post by colin.p on 2010-07-28
I set up a dual boot with 10.04 PAE with win 7 on a Dell Laptop. I also was going to use the win boot loader with EasyBCD and installed grub to sda5, the / psrtition. I couldn't get Easy BCD to work as Dell has a weird partition arrangement, so I decided to re-install ubuntu and put grub in sda. However, I decided to install 10.04 X64 instead and still put grub in sda.(I installed the 64 bit version over top of the PAE and didn't format)
After an episode with cantankerous win 7 and Dell Data Safe sabotaging the boot up, I got everything sorted out.
However, grub now shows the X64 kernels and the PAE kernels as well. So I think the grub in sda, sees the grub(?) in sda5 and the reference to the PAE kernel, that of course is no longer there.
So, how do I get rid of the reference to the PAE kernel, or get rid of the second grub, if it actually is still there?

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63b76f8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       22197   162889048    7  HPFS/NTFS
/dev/sda4           22198       38913   134271239+   5  Extended
/dev/sda5           22198       25005    22555228+  83  Linux (/)
/dev/sda6           25006       25561     4466038+  82  Linux swap / Solaris
/dev/sda7           25562       38913   107249908+  83  Linux  (home)

---

### Post by chopinhauer on 2010-07-28
> **colin.p said:**
> 
So, how do I get rid of the reference to the PAE kernel, or get rid of the second grub, if it actually is still there?


My guess is you have still some 32 bit kernels in your /boot directory, since you didn't reformat the filesystem. Hence **update-grub** adds them to the menu too. Just delete the kernels (and the respective /lib/modules directories) and rerun:
```

sudo update-grub

```
**[SIZE=4]Attention:[/SIZE]**[SIZE=4][SIZE=1] [SIZE=2]Be careful not to delete the kernel you are using right now and it's easier to delete the other 64 bit kernels with **apt-get**

[/SIZE][/SIZE][/SIZE]

---

### Post by colin.p on 2010-07-28
That did it, thanks alot

---

