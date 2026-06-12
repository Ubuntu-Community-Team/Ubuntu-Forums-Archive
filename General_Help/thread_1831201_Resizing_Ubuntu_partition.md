---
title: "Resizing Ubuntu partition"
date: 2011-08-23
forum: General Help
---

### Post by queenofbabes on 2011-08-23
Hi,

I currently have 3 main partitions: 1 for windows, 1 for Ubuntu and 1 just for storing files. If it helps, I'm attaching a screenshot of what it looks like in gparted.

I want to shrink the 'files' partition (/dev/sda5) and add it to the Ubuntu partition(/dev/sda7). I have read that resizing Windows partition leads to boot problems that need to be repaired, etc. Does the same apply to partitions with existing Ubuntu installations? Is there anything else I should watch out for?

Thanks in advance!

---

### Post by Mark Phelps on 2011-08-23
IF indeed, /sda5 is just a data partition, you have a couple of choices.

The safest would be to use the Win7 Disk Management utility to shrink it.  Since it's not an OS partition, it should allow you to shrink it quite a lot.

The other choice is to use Gnome Partition Editor (GParted) to shrink it.  Since it's not an OS partition, it doesn't need to boot -- so GParted should be able to handle it without problems.

It's also a good idea to back off the contents of any partition before you mess with it -- just to be safe.

---

### Post by Basher101 on 2011-08-23
> It's also a good idea to back off the contents of any partition before you mess with it
don't you mean ***_back up_***? Otherwise there is nothing i could add. Just do as he said

---

### Post by oldfred on 2011-08-23
I am not a fan of large / (root) partitions. Your 30GB is a good size if you are storing all you data in your shared NTFS partition. If you are planning on having a fair amount of Linux only data you might consider a /home partition or just  a /data partition for Linux data.

You also have two swaps. The one you are using sda8 is adjacent to your root, but you could change to the other one by editing fstab with the UUID of sda6. Then you could easily add the 7GB of swap to your root.

To see your UUID and partitions:
sudo blkid
sudo fdisk -l
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

You will have to do all the editing of partitions from a liveCD, since root & swap are in the extended partition. You also will have to click on swap and right click swap off as liveCDs use swap if found to speed things up.

---

### Post by queenofbabes on 2011-08-24
Alright, thanks guys for all the info!

---

