---
title: "Mount Hard Disk?"
date: 2006-02-20
forum: General Help
---

### Post by jasrog on 2006-02-20
In able to put files on an available hard drive I partitioned to Fat32 format in ubuntu it has to be mounted right? If so how exactly do i mount it?

---

### Post by user.foo on 2006-02-20
in a terminal:

$ sudo mkdir /media/hdxz
(x being the which hard disk, z being the partition)

$ sudo mount /dev/hdxz /media/hdxz
(x being the which hard disk, z being the partition)

---

### Post by jasrog on 2006-02-20
I am lost...the one I want to mount is partition 5 /dev/sda5 how would I do that?

---

### Post by LordBug on 2006-02-20
Following user.foo's example:

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5

The mountpoint (/media/sda5 in this case) can be just about anywhere, named just about anything.  Personally, I use the /mnt directory for things like this, but you're free to do it however fits you.

---

