---
title: "Debian's grub is missing Ubuntu 9.10 entry"
date: 2009-11-15
forum: General Help
---

### Post by Andreas1 on 2009-11-15
Hi,
I have ubuntu 9.10 installed and i just installed debian 5, and the grub installed by debian is missing entries for ubuntu. is that because of ubuntu using grub 2, or ext4? anyway, what do i do?

i know i could restore ubuntu's grub using a live cd, but i'd prefer fixing this within debian, so i don't have to reboot. so how can i add ubuntu 9.10 to an old grub on another os? i already tried running update-grub in debian, but it does not detect ubuntu.

---

### Post by Andreas1 on 2009-11-25
bump

---

### Post by mechro on 2009-11-25
You could add a chainloader entry in your Debian menu.lst. Here's an example of Ubuntu installed on sda1 with root and bootsector both on sda1...

```
# This entry manually added
# linux installation on /dev/sda1.
title		Ubuntu
root		(hd0,0)
chainloader	+1
```

---

### Post by ranch hand on 2009-11-25
Lenny has no support for ext4.  Can't see it at all.  I would change to the Ubuntu grub2, it should have no trouble with picking up Lenny.

Use these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by QLee on 2009-11-25
Well, here is the description for the version of e2fsprogs in Lenny, currently 1.41.3-1.

--
e2fsprogs
ext2/ext3/ext4 file system utilities
The ext2, ext3 and ext4 file systems are successors of the original ext
("extended") file system. They are the main file system types used for
hard disks on Debian and other Linux systems.

This package contains programs for creating, checking, and maintaining
ext-based file systems, and the generic fsck wrapper.
--

Poster mechro's advice looks reasonable to me, chainload to the GRUB on the 9.10 partition.

---

### Post by oldfred on 2009-11-25
For the chainload to work grub2 has to be in the partition. And grub2 does not like to be in partitions. I installed it to my Karmic alpha install and it complains everytime about blocklists being "BAD" but they may not be. It has worked for me, but I understand they have made it even more difficult to install to a partition. It will required a --force parameter in the command to install grub2.

---

### Post by mechro on 2009-11-25
> **oldfred said:**
> For the chainload to work grub2 has to be in the partition. And grub2 does not like to be in partitions. I installed it to my Karmic alpha install and it complains everytime about blocklists being "BAD" but they may not be. It has worked for me, but I understand they have made it even more difficult to install to a partition. It will required a --force parameter in the command to install grub2.

So Grub2 prefers the bootsector in the MBR?? I don't like the sound of that. All my installations are chainloaded from a Grub partition.:-(

---

