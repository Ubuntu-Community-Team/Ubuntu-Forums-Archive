---
title: "Partition Permissions"
date: 2009-12-24
forum: General Help
---

### Post by Mahngiel on 2009-12-24
Can't seem to get permission to create / make changes to my storage partition (sda2) which i have set up to auto mount on boot.

fdisk, fstab, and view of my inability to create a folder shown below.

--thanks.

[[IMG]http://i806.photobucket.com/albums/yy341/mahngiel/th_9c361641.png[/IMG]]("http://s806.photobucket.com/albums/yy341/mahngiel/?action=view&current=9c361641.png")

---

### Post by bodhi.zazen on 2009-12-24
Ownership and permissions of FAT partitions are set at the time of mounting.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Morbius1 on 2009-12-24
Change 

/dev/sda2 /media/storage vfat auto,users,nosuid,rw 0 0

To 

/dev/sda2 /media/storage vfat utf8,umask=007,uid=1000,gid=46 0       0

The umask = 007 will give owner and group read / write permissions
The uid = 1000 ( which really isn't necessary but comes in handy if you ever decide to share this partition on your network ) will make you ( 1000 ) the owner.
And gid=46 is the group that all users on your system belong to.

Anyway, that's what I'd do. :)

---

### Post by bodhi.zazen on 2009-12-24
> **Morbius1 said:**
> Change 

/dev/sda2 /media/storage vfat auto,users,nosuid,rw 0 0

To 

/dev/sda2 /media/storage vfat utf8,umask=007,uid=1000,gid=46 0       0

The umask = 007 will give owner and group read / write permissions
The uid = 1000 ( which really isn't necessary but comes in handy if you ever decide to share this partition on your network ) will make you ( 1000 ) the owner.
And gid=46 is the group that all users on your system belong to.

Anyway, that's what I'd do. :)

If you do not wish all your fiels to be marked as executable, use fmask and dmask rather then umask :-\"

---

### Post by Mahngiel on 2009-12-24
> **Morbius1 said:**
> Change 

/dev/sda2 /media/storage vfat auto,users,nosuid,rw 0 0

To 

/dev/sda2 /media/storage vfat utf8,umask=007,uid=1000,gid=46 0       0



Thanks, do i need to keep "auto" in there? i'm assuming so moving forward.

edit: after reboot, this worked like a charm, thanks. didn't really find a need to worry about files being non-executable, thanks for the intel tho bhodi - always great to learn new things.

---

### Post by Morbius1 on 2009-12-24
nope

[COLOR=Blue]EDIT: it won't hurt anything if it's there however.[/COLOR]

---

