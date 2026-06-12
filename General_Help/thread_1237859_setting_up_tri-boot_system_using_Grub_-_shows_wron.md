---
title: "setting up tri-boot system using Grub - shows wrong loading screen / freezes"
date: 2009-08-11
forum: General Help
---

### Post by Braeden2 on 2009-08-11
I had kubuntu 9.04 and win 7 dual booting working fine with grub. I am now trying to add fedora 11 to the mix. Currently fedora shows up in grub, however when I select it a kubuntu loading screen appears, followed by the initial first run setup of fedora (setting up users, etc.). This screen is frozen off the bat, cannot move cursor and keyboard unresponsive.

My partition layout is a bit of a mess, but as far as I know should be working fine:
*I installed fedora from a live cd, a cd which required a small ext3 /boot partition and a larger ext4 / partition. (My understanding of this is it just copies the files from cd to the / partition, so requires the same filesystem on it.)


```
   Device Boot      Start         End      Blocks   Id  System
               /dev/sda3               1        8317    66806271    5  Extended
kubuntu        /dev/sda5               1        3911    31415044+  83  Linux
swap           /dev/sda6            3912        4425     4128673+  82  Linux swap/Solaris
fedora /       /dev/sda7            4426        8317    31262458+  83  Linux
fedora /boot   /dev/sda4            8318        8342      200812+  83  Linux
data           /dev/sda1            8343       25570   138383910    7  HPFS/NTFS
win7           /dev/sda2   *       25571       30401    38805007+   7  HPFS/NTFS
```

As can be seen above, kubuntu, swap partition and fedora / partition are in a single logical partition, whilst fedora /boot, data and win7 each have there own primary partition.


My grub/menu.lst:

```

default 0
timeout 2

title           Ubuntu 9.04, kernel 2.6.28-14-generic
uuid            16d42441-ade5-4ab0-ab19-fb7a2c012658
kernel          /boot/vmlinuz-2.6.28-14-generic root=UUID=16d42441-ade5-4ab0-ab19-fb7a2c012658 ro quiet splash

initrd          /boot/initrd.img-2.6.28-14-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid            16d42441-ade5-4ab0-ab19-fb7a2c012658
kernel          /boot/vmlinuz-2.6.28-14-generic root=UUID=16d42441-ade5-4ab0-ab19-fb7a2c012658 ro  single
initrd          /boot/initrd.img-2.6.28-14-generic

title           Fedora 11, kernel 2.6.28-14-generic
kernel         (hd0,4)/boot/vmlinuz-2.6.28-14-generic root=/dev/sda7 ro quiet splash
initrd          (hd0,4)/boot/initrd.img-2.6.28-14-generic



title           Other operating systems:
root

title           Windows 7
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader     +1

```

Is the behavior I am seeing a problem with grub, my fedora install or my partition layout? Perhaps a combination of them?

Any help would be much appreciated.

---

### Post by oldfred on 2009-08-12
I do not use Fedora, but its boot is sda4 so your menu.lst entry for fedora should be (hd0,3) if it boots from sda4.

It looks like (hd0,4) or sda5 is your kubuntu so that is why fedora is confused when it tries to boot.

---

### Post by Braeden2 on 2009-08-12
Thanks for the reply,

After posting that I re-read what I had and caught that mistake. Using (hd0,3) it gave me a file not found error after selecting Fedora.

I think I may just blow away all partitions bar data and win7 and start from scratch, with a little planning this time, possibly scraping kubuntu all together.

Thanks again for the reply.

---

### Post by oldfred on 2009-08-13
I forgot that Fedora has a separate boot partition. Yours is sda4 so your boot should  be (hd0,3)

---

