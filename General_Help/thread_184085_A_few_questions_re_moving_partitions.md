---
title: "A few questions re moving partitions"
date: 2006-05-29
forum: General Help
---

### Post by khedron on 2006-05-29
I'm thinking of repartitioning my hard drive. In order to move my Ubuntu installation to another partition, I envisage: a) Moving / to a backup partition on another drive, b) Repartitioning the hard drive, and c) Copying / back onto the new partition. I have a few questions:

1. Does Grub care where the root filesystem is mounted? As in, if I move everything in partition 5 to partition 3, with the same filesystem, will I need to reinstall Grub?

2. Am I right in thinking that the only places where hd partitions are mentioned in the filesystem are /boot/grub/menu.lst and /etc/fstab ? So if I change these two to reflect the new partition layout, should everything be fine?

3. In my current understanding, everything except for /home is owned by root. So if I backed up my filesystem by copying it to another partition, could I keep the default permissions when I copied it back by copying under sudo and doing 
"sudo chmod -R 0755 / ; sudo chmod -R 0777 /home" afterwards? (The second command would be to allow me to log on afterwards; I would then chown the /home directory when logged on.)

---

### Post by olsonar on 2006-05-29
It'd acually probably be easier for you to just copy the contents of your /home directory (or put it on a [separate partition)]("http://ubuntuforums.org/showthread.php?t=169053") , then do a full reinstall, redoing the partitions as you do so, then restoring the /home directory (if you put it on a separate partition, be sure to tell ubuntu to mount it as /home during the install).

anyway, to answer your questions:

1) yes

2)i think so

3)i don't know

---

### Post by aysiu on 2006-05-29
I would recommend using PartImage to copy your entire partition image instead of copying files.
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

You can always modify the /etc/fstab and /boot/grub/menu.lst later.

You can also re-install Grub to the MBR:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by khedron on 2006-05-29
Cool, thanks.

I would try to use PartImage, but I am planning on resizing my Ubuntu partition, so that wouldn't work.

---

### Post by aysiu on 2006-05-29
[QUOTE=khedron]Cool, thanks.

I would try to use PartImage, but I am planning on resizing my Ubuntu partition, so that wouldn't work.[/QUOTE] PartImage will copy only the part of the partition that's being used.

So if you have a 10 GB partition and you're using only 6 GB of it, the partition image will be 6 GB, not 10 GB.

---

