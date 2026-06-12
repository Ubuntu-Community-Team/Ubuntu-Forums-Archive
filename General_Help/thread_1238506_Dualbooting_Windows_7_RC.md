---
title: "Dualbooting Windows 7 RC"
date: 2009-08-12
forum: General Help
---

### Post by RandomCoolName on 2009-08-12
i had a computer with three partition, one with vista, one with windows 7 rc, and one for general storage. i installed ubuntu on the vista partition, which was my main partition. now i can only access the ubuntu partiton. from my bios i can only select the hard drive, not the indivifual partitions in the booting device priority, so i have no idea what to do. this was my first linux install...


someone told me i should post this as well (from terminal)

bruno@linux-bruno:~$ sudo fdisk -l
[sudo] password for bruno: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c9a53fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         608     4883728+   5  Extended
/dev/sda2           12749       25497   102400000    7  HPFS/NTFS
/dev/sda3           25497       60802   283583488    7  HPFS/NTFS
/dev/sda4   *         609       12748    97514550   83  Linux
/dev/sda5               1         608     4883697   82  Linux swap / Solaris

Partition table entries are not in disk order
bruno@linux-bruno:~$ 

any help/insight will be greatly appreciated

---

### Post by oldfred on 2009-08-12
We would also like to see /boot/grub/menu.lst

```
cat /boot/grub/menu.lst
```
When I installed Ubuntu it found all the windows I had installed and added entries like these at the bottom of menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
chainloader    +1

You have windows in sda2 and sda3 so the numbering in grub will be (hd0,1) and (hd0,2), Grub counts from zero, linux from 1

Your Win7 entry should be like this:

title        Windows 7 Ultimate, chainloader (on /dev/sda3)
rootnoverify    (hd0,2)
savedefault
chainloader +1

If you want to try to edit before posting:
backup first
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

``````
gksudo gedit /boot/grub/menu.lst
```

---

