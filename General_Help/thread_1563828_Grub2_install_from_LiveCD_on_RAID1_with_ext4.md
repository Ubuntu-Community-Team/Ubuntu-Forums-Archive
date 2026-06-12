---
title: "Grub2 install from LiveCD on RAID1 with ext4"
date: 2010-08-29
forum: General Help
---

### Post by hurgler on 2010-08-29
Hi!

I received from a friend an installation of edubuntu (Ubuntu 10.04). I  just had to set up a RAID 1. All seems to have worked fine. I can access  all my mirrors and they are in sync.

My configuration:
md0  sda1/sdb1 --> /boot  --> ext2
md1  sda2/sdb2 --> /        --> ext4
md2  sda3/sdb3 --> swap

Where I have my problems is booting the system. Accessing the data on  md0/md1 is possible from Live CDs as Knoppix or the Ubuntu Desktop Live  CD.

I tried several things, but I think that grub2 has problems finaly with the ext4 Filesystem.

1.) update-grub and grub-mkconfig aren't working, as you can't direct them to other places of the root Filesystem
2.) chroot and update-grub or grub-mkconfig resulted also in an error
3.) grub-install from the live-cd or knoppix also not resulted as expected.
I tried "grub-install --root-directory=/dev/md1 --modules=mdraid  /dev/sda" (also tried instead of sda /dev/md1 but not with more success)

So I tried also using the rescue mode of grub2 in which at least I entered...
I tried the following:

set prefix=(hd0,1)/grub
set root=(hd0,2)
insmod (hd0,1)/grub/linux.mod --> at least this succeded
linux /vmlinuz root=/dev/md1 ro--> no such file (but in / of md1 exists a /vmlinuz)
neither works: linux (hd0,2)/vmlinuz --> no such file

I do not know how to continue. Please help. Hope I don't have to change  ext4 to something else. Nor to change grub2 back to grub1...

Thanks in advance...
Matthias

---

