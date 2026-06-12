---
title: "Another GRUB error.."
date: 2009-09-08
forum: General Help
---

### Post by snowie72 on 2009-09-08
Hi this is my fdisk, sda5 should be my Windows XP boot, but it gives me error 12 and error 13, when ever I try to boot from it.. I tried multiple others fixes nothing is coming to light.. Also after I installed Ubunbtu I deleted a second partition of XP which I used as a back-up. I beleive that maybe my boot.ini was in there, just thought I would add this incase its relevant.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81b168db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   828318960   834306479     2993760   82  Linux swap / Solaris
/dev/sda2              63   828318959   414159448+   f  W95 Ext'd (LBA)
/dev/sda5        14348943   828318959   406985008+   7  HPFS/NTFS
/dev/sda6             189    14348879     7174345+  83  Linux

Partition table entries are not in disk order

Also, this is what my menu.lst looks like.

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		aea83b3d-8385-48dc-a36b-06bddb61834b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=aea83b3d-8385-48dc-a36b-06bddb61834b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		aea83b3d-8385-48dc-a36b-06bddb61834b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=aea83b3d-8385-48dc-a36b-06bddb61834b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		aea83b3d-8385-48dc-a36b-06bddb61834b
kernel		/boot/memtest86+.bin

title Windows XP
rootnoverify (hd0,7)
makeactive
chainloader +1

---

### Post by uncle-c on 2009-09-08
title Windows XP
rootnoverify (hd0,[COLOR="Sienna"]4[/COLOR])
makeactive
chainloader +1 

If you want to boot into XP replace the 7 with 4.

---

### Post by snowie72 on 2009-09-08
I tried adding it to my menu.lst, same error appears.

Could it be something to do with my Boot.ini?

---

### Post by snowie72 on 2009-09-08
Anyone have any ideas? Do you need me to post more information?

---

### Post by uncle-c on 2009-09-08
Try changing [COLOR="Sienna"]rootnoverify (hd0,4)[/COLOR] to [COLOR="Sienna"]root (hd0,4)[/COLOR]. Also use fdisk to make /dev/sda5 the active partition boot partition.

ps : do you boot into ubuntu ok ?

---

