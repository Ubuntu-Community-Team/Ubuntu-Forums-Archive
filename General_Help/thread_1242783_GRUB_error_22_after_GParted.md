---
title: "GRUB error 22 after GParted"
date: 2009-08-17
forum: General Help
---

### Post by johnvan on 2009-08-17
I just messed up my computer. I dual boot Vista and Ubuntu and I rarely use Vista so I decided to make my Ubuntu partition bigger with Gparted.  After a few changes my Ubuntu partition is now /dev/sda4 as opposed to /dev/sda5. This gives me a Grub error 22.
I can start my computer with the Super grub rescue disk but can't fix it.
Here's what I get in Fstab;
[B][I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda5 during installation
UUID=399b9b11-92db-4bd2-b7b0-b9dbbccf69f4  /              ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda6 during installation
UUID=4153f824-2564-4046-9e24-a50192029d49  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda1                                  /media/sda1    ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  [/I][/B]

I'm really new at this but I guess I either need to point grub to the right partition or change the name of the partition back to /dev/sda5. How do I do this, the simpler the better.

Thanks

---

### Post by ajgreeny on 2009-08-17
Start with the ubuntu live CD and run ```
sudo fdisk -l
```to see what is on what partition, then run```
sudo blkid
```to get the UUIDs of the partitions.  Now you may need to edit the **/etc/fstab** to ensure that the swap and root partitions are correct for a start, and also need to ensure that **/boot/grub/menu.lst** points to the correctly numbered partition, UUIDs now being the default in grub, instead of the older **root (hd0,0)** system used previously. You can still use the old root (hd0,0) system if you prefer.

---

### Post by johnvan on 2009-08-17
Thanks, I managed to fix it.

---

