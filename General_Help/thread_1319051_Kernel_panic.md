---
title: "Kernel panic"
date: 2009-11-08
forum: General Help
---

### Post by pontusgustafsson on 2009-11-08
hi all, need some help to get into ubuntu 9.10.
After choosing ubuntu in grub I get the following error
 
[2.149105] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2)
 
when I restart and press e I can see the following
insmod ntfs
set root=(hd0,2)
search -- no floppy --fs-uuid --set881e2cd01e2cb958
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinux -2.6.31-14-generic root=/dev/sda2 loop =/ubuntu/disks\
/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
 
My Ubuntu is a windows installation on Vista
Worked fine for a long time then. Think it was during a couple of upgrades it stopped working.
 
Please help
 
Cheers
Pontus

---

