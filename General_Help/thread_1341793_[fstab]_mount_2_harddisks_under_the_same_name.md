---
title: "[fstab] mount 2 harddisks under the same name"
date: 2009-11-30
forum: General Help
---

### Post by jackel7007 on 2009-11-30
On our server we have 2 backup hard-disks which are rotated.
We would like to mount these 2 hard-disks under the same name:
/media/backup

I have added both hard-disks to the fstab file, using the UUID.
After changing the hard-disk the server is rebooted.

I have manually created the /media/backup folder. 
And Added the following lines to fstab:

# ---- backup HD 1 ----
UUID=1308-0351      /media/backup vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1002,utf8,umask=077,flush 0 0
# ---- backup HD 2 ----
UUID=1407-3508      /media/backup vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1002,utf8,umask=077,flush 0 0

The disk is mounted correctly under the user 1002.
But the backup proces, areca, which runs trough cron has no access to the disk.
How can i change the fstab so areca has access?

---

### Post by jamesisin on 2009-11-30
Have you checked the permissions of /media/backup?  If that is set to rw - - (which quite often it is) then you could see this issue.

---

### Post by jackel7007 on 2009-11-30
I can only change the permissions of the folder /media/backup if no disk is connected to it.
As soon as i connect a disk, the permissions change, and i can't adjust them.

---

### Post by jamesisin on 2009-11-30
What happens when you attempt to apply permissions?

What permissions are currently in place (for each drive)?

---

### Post by jackel7007 on 2009-11-30
if I run a

sudo chmod 777 /media/backup

I get no error or message, but it leaves it like it was.
and that is 700

---

### Post by sisco311 on 2009-11-30
You can not mount 2 partitions/disks in the same directory.

To combine two or more physical hard disks into a single logical unit you have to use LVM or RAID 0.

---

### Post by jamesisin on 2009-11-30
sisco - Isn't that only the case if both drives are attached simultaneously?  In this case the user swaps the two drives (and each should be able to mount in its turn using the same name).

---

### Post by jamesisin on 2009-11-30
You're using FAT32?  Is that necessary?  FAT can't do Unix permissions (or permissions in general, as I understand it).  But I think we are on the right track, because 700 is likely to cause the issues we are discussing.

---

### Post by sisco311 on 2009-11-30
> **jamesisin said:**
> sisco - Isn't that only the case if both drives are attached simultaneously?  In this case the user swaps the two drives (and each should be able to mount in its turn using the same name).

Oh, you are right, I misread the OP.

---

### Post by jamesisin on 2009-11-30
These things happen...

---

### Post by jackel7007 on 2009-11-30
I am trying this for some time now, and last week all went fine using the fstab in the OP.
After changing the disks on friday, i found out today that there was an error in the backups this weekend.

So it seems one disk is doing fine, but the other one is failing..
the two disks are exact the same...

It looks like it also has to do with the rights on the backup folder, which is used by areca.
this folder is also 700, and since cron is running the tasks, i think it shoud be 770 or 777 .

trying to change the folder using

sudo chmod 777 foldername

gives no error, but just doesn't work...

---

### Post by jamesisin on 2009-11-30
Try wiping the partition and rebuilding it.  Be sure to choose the take ownership option when you do so.

---

