---
title: "Grub Chainloading"
date: 2006-03-21
forum: General Help
---

### Post by zachtib on 2006-03-21
I have ubuntu installed on /dev/hda1 and grub is on the MBR of /dev/hda
I have logical partitions (10gb each) on /dev/hda5 and /dev/hda6 for testing other distributions and development versions w/o messing with my stable installation.

When I install another distro, I want to have it install GRUB to the partition it is on rather than the MBR of my hard drive, as that would overwrite breezy's grub, which I want to remain the default, so I wrote this into menu.lst:

```
title		Ubuntu 5.10 (Breezy Badger)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Chainload Second Partition
root		(hd0,4)
makeactive
chainloader	+1

title		Chainload Third Partition
root		(hd0,5)
makeactive
chainloader	+1

```

Will this work the way I think it should?

The reason I want to do it this way, is so that whenever one of my distros updates it's kernel, I will be able to access the new one.  For example, id dapper overwrites breezy's grub, and I update breezy's kernel, then the chnage is written to /boot/grub/menu.lst on breezy's partition, which dapper's grub would not see.

Also, I try out new distros constantly, and this would make my setup a little saner.

---

