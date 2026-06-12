---
title: "Restore partitions, swap and grub2"
date: 2010-10-27
forum: General Help
---

### Post by homemrobo on 2010-10-27
Hi there, first, I'm in love with linux. Second, I'm still a linux noob.. :)

Unitl yesterday I have a pc with ubuntu server and desktop. Server I installed first. Desktop later. But I want to remove that server and use the space for other stuff..

I mess with Disk Utilities and gParted and remove the ubuntu server partition. But now my grub2 stops working. 

How can I restore grub2 on the desktop partition and use the unallocated space for desktop without loosing any of my stuff? I have a scanner, webserver running, samba and other apps up and running on desktop.

I can boot via live cd, and I get this on sudo fdisk -l:

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006ec42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4742    38085937+  83  Linux
/dev/sda2            4742        9726    40036353    5  Extended **(unallocated space)**
/dev/sda5            4743        9324    36804915   83  Linux** (my desktop ubuntu)**

And my grub2 now, can't boot. This is what I get:

grub rescue>ls
(hd0) (hd0,5) (hd0,1)

How can I:
- tell grub "look, boot from here now"
- look ubuntu, now you have to use this swap parition
- look unallocated space AND ubuntu partition, now you are the same...

Thanks

Homem Robô

---

### Post by linux-hack on 2010-10-27
Well you could make a ext4 file system from the unallocated space.

And for Grub just install it on the first partition. From the live type in a terminal :
```

mount -t ext4 /dev/sda1 /mnt
grub-install --root-directory=/mnt /dev/sda1

```

The server that you deleted was on /dev/sda1 ? If yes you can reformat the partition to make it 100M or 200M to have more space and install grub in it. With the rest of the place you just make another partition for your stuff.

---

### Post by linux-hack on 2010-10-27
Take a look at this : [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

or even better : [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by homemrobo on 2010-10-27
Hi there, my server was on the /dev/sda2  not in /dev/sda1 . I'll check these links, thanks. 

But my swap partition is gone. I can create another one later right?



[]'s

Mateus

---

### Post by homemrobo on 2010-10-27
Hi, this is what I get when I try 

grub-install --root-directory=/mnt /dev/sda1

/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

[]'s

Mateus

---

### Post by drs305 on 2010-10-27
If your current Ubuntu installation is on sda5, then these are the commands you want to run:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note you do NOT put the partition number in the second command.

Yes, you can make the swap partition after you get Ubuntu booting correctly. You will make a partition and put the swap entry into fstab.

---

### Post by homemrobo on 2010-10-27
@drs305

Thanks! That did the magic! It's working fine now. 

I use gParted to get rid of all extra partitions. Then I use Disk Utilities to create a swap partition and a new partition for "backups" with the extra space. 

Really thanks guys. 

Btw, linux is really fast, give another life for my p4.

[]'s

Mateus

---

### Post by linux-hack on 2010-10-27
Glad to help :D

And thanks for the correction **drs305**

---

### Post by drs305 on 2010-10-27
> **homemrobo said:**
> Then I use Disk Utilities to create a swap partition and a new partition for "backups" with the extra space. 


One thing you might want to check is whether swap is now working. Use this command to see if swap is available. It should be OK unless *all* the numbers are zero.
```
free -m
```

If you suspect a problem, you can compare your swap UUID with the one stored in your system. Make sure the numbers match:
```
sudo blkid -c /dev/null | grep 'swap'  && cat /etc/initramfs-tools/conf.d/resume

```

If they are different, change the UUID in the following file to match the "blkid" result:
```
gksu gedit /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -u

```

If you don't have any problems with this, please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.  :-)

---

