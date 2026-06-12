---
title: "Changing Ownrship  NTFS Volume"
date: 2010-10-04
forum: General Help
---

### Post by Quarkrad on 2010-10-04
(Ubuntu 10.04)  I would like to change to change the ownership of one of my storage partitions from **root** to **dad**  - I am currently reading through as much Ubuntu documentation as I can but the process is slow. If I gksudo nautilus and select the drive, right click/properties/Permissions the owner is set to root.  If I try to change the group ownership from root to dad it looks like it momentarily does it but it stays at root.  A doc suggested using Pysdm as a gui for fstab - but so far I have only found out how to allow other users to mount the volume  not own it.   My fstab entry for this volume reads as  **/dev/sdb6  /media/backuphd2      ntfs-3g  group=dad,users,user,owner  0  0** - it looks to me that in terms of ownership, root = 0  0   Can I find out what the ownership of dad is in terms of numbers (e.g. owner 0  1  or owner  1  1) and then change the fstab entry?   Is it as easy(?) as this?  I will carry on reading.  Thanks

---

### Post by sikander3786 on 2010-10-04
See here.

[http://ubuntuforums.org/showthread.php?t=913652](http://ubuntuforums.org/showthread.php?t=913652)

This one works for me on ext3/ext4 drives. Not sure if it works with NTFS also (it should work?). Can anybody confirm?

```
sudo chown -R <username>:<username> /media/xxx
```

---

### Post by sisco311 on 2010-10-04
You can set the owner & group with the uid & gid options and the permissions with umask/dmask/fmask. See: [thread=283131]How to fstab[/thread].

Also device names (/dev/sdXY) may change between system boot, so use UUIDs in the fstab. [uhelp]community/UsingUUID[/uhelp]

i.e.:
```
UUID=**uuid-of-the-partition** /media/backuphd2 ntfs-3g defaults,uid=**dad**,gid=**dad**,dmask=002,fmask=113 0 0
```

You can get the uuid of the partition with the blkid command:
```
sudo blkid /dev/sdb6 -c /dev/null
```

---

### Post by Quarkrad on 2010-10-04
Thank you.  I have previously tried the chown commands but had no luck.  I looked up the uuid of /dev/sdb6 and entered the terminal command - this was the output: 

[B] root@dadubuntu:/home/dad# UUID=01CA5FC0DB3C4480 /media/backuphd2 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
bash: /media/backuphd2: is a directory[/B]

The last comment is interesting - backuphd2 is a partition not a directory.

---

### Post by sisco311 on 2010-10-04
> **Quarkrad said:**
> Thank you.  I have previously tried the chown commands but had no luck.  I looked up the uuid of /dev/sdb6 and entered the terminal command - this was the output: 

[B] root@dadubuntu:/home/dad# UUID=01CA5FC0DB3C4480 /media/backuphd2 ntfs-3g defaults,uid=dad,gid=dad,dmask=002,fmask=113 0 0
bash: /media/backuphd2: is a directory[/B]

The last comment is interesting - backuphd2 is a partition not a directory.

That's not a command but an fstab entry, edit the file:
```
gksu gedit /etc/fstab
```

Replace the old entry with the new one and remount the partition:
```
sudo umount /media/backuphd2
sudo mount -a
```

---

### Post by Quarkrad on 2010-10-04
Solved - many thanks.  I will now read the doc' s and the command you gave me to try and work out all this hangs together - appreciated.

---

