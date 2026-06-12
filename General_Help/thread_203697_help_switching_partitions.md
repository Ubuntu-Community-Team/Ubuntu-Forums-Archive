---
title: "help switching partitions"
date: 2006-06-25
forum: General Help
---

### Post by scpike on 2006-06-25
I have a 80 gb hard drive in this laptop.
it is currently partitioned into 4 parts

/dev/sda1 has windows xp   (20 gb) 
/dev/sda2 is a fat32 partition (40 gb) 
/dev/sda3 is a ext3 partition with ubuntu on it (19 gb)
/dev/sda4 is a swap partition (<1 gb)

I want to get rid of the fat32 partition, move the ext3 one in its place, and then create a new ext3 partition after the ubuntu one to install suse on, and then make a smaller fat32 partition after that.  is there a command to copy all of /dev/sda3 into a new partition at /dev/sda2? dd does something like that right? any help would be appreciated

---

### Post by aysiu on 2006-06-25
I think PartImage would be a safer option--you might have to change the /etc/fstab and /boot/grub/menu.lst to reflect the partition changes, though.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by scpike on 2006-06-25
thats a really nice guide, much appreciated, if i have any problems ill post again, if not, thanks for the help

---

