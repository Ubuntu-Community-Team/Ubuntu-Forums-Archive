---
title: "windows won't boot from grub"
date: 2009-08-01
forum: General Help
---

### Post by jpdamigaman on 2009-08-01
HI I tried to over clock my pc last week.

When I tried to boot windows again the grub disappeared.

I used super grub disk to boot windows.

I have 2 hard drives in my pc
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ec11ec0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sda5               2        9729    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc6ee3e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1980    15904318+   7  HPFS/NTFS
/dev/sdb2            1981        9953    64043122+   f  W95 Ext'd (LBA)
/dev/sdb3            9954       12563    20964825   83  Linux
/dev/sdb5            1981        9813    62918541    7  HPFS/NTFS
/dev/sdb6            9814        9828      120456    b  W95 FAT32
/dev/sdb7            9829        9834       48163+   b  W95 FAT32
/dev/sdb8            9835        9953      955836   82  Linux swap / Solaris

If I remove 2nd drive 80 GB(ide) I can edit grub before windows or ubuntu boots and change menu list and windows and ubuntu boots but when I plug in My 2nd drive windows won't boot but ubuntu will.

main 160 GB drive is SATA

windows xp just hangs with no message

menulist

default 1
fallback 2
timeout 10

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd1,0)
chainloader +1
savedefault
makeactive

title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

---

### Post by merlinus on 2009-08-01
With your second hdd plugged in, you need map statements to make windows believe it is the only one.

So

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by jpdamigaman on 2009-09-07
solved

---

