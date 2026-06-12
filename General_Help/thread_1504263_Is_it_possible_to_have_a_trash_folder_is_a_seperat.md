---
title: "Is it possible to have a trash folder is a seperate partition to the operating system"
date: 2010-06-07
forum: General Help
---

### Post by ozguitarplayer on 2010-06-07
Hi,
When I set up my hdd for multi-boot (2xlinux)I also created a separate partition for all my data so it could be accessed from either o/s. I did this because I wasn't clever enough to place Home in the data partition.

This means that when I delete from the data partition it does not go to Trash.

Is it somehow possible to delete to Trash, or can I set up a Trash folder in the data partition?

---

### Post by drs305 on 2010-06-07
Do you have a .Trash-<uid> folder in the partition? If you are the first user (uid=1000) then you may have a .Trash-1000 folder into which your user deleted files are being moved to.

For root trash, it would be in the partition's /root/.local/Share/trash folder.

Of course, they are hidden folders so make sure your file browser is set to view them (Nautilus: CTRL-h).

---

### Post by ozguitarplayer on 2010-06-07
thanks drs305,
I have in that partition .Trash-0 which has a few files in it from Feb this year and I guess ones that were delete as root.
Can I change the settings so that I can delete to it as user also?

---

### Post by drs305 on 2010-06-07
> **ozguitarplayer said:**
> thanks drs305,
I have in that partition .Trash-0 which has a few files in it from Feb this year and I guess ones that were delete as root.
Can I change the settings so that I can delete to it as user also?

If you delete something as a normal user the .Trash-1000 folder should be created. Try copying one of your user files and then delete it and see if the folder is created. If it isn't, check your normal user trash bin and make sure it didn't end up there.

---

### Post by ozguitarplayer on 2010-06-08
I've had this o/s system installed for about 6 months and done many deletes so the .Trash-1000 should have been created by now.
Just now I have done some more deletes and the files do not appear in either the Trash folder in with the o/s nor the Trash folder in the data partition.
Just to be clear; I can delete to the Trash folder in the o/s when working in Home, it's when working in the data partition where I cannot delete to either Trash folder.

---

### Post by drs305 on 2010-06-08
For ntfs and vfat formats (and perhaps other non-linux formats) it may be necessary to add "uid=1000" to the options in fstab.  

Assuming your partition is an ext2/3/4 partition, I would guess it's already in fstab if it's an internal drive. If it's an external drive, you might try adding it to fstab. I have a .Trash-1000 folder in each of my ext4 partitions which automatically appear. 

Notes:
I only have the uid option entered in the non-linux partition entries.
In my linux partitions, I do have "users" in the options section.

---

### Post by ozguitarplayer on 2010-06-08
Thanks for that drs305,
Here is the fstab, it's /dev/sda6 that I use for data

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=7e110498-aacf-4165-82cc-779d3a2781d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3a007576-2387-4f87-9bc1-d1a079e4736e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda6	/media/nifi	ext3	user,auto	0	0

```

---

