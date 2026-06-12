---
title: "How to back-up running system"
date: 2010-04-20
forum: General Help
---

### Post by DeMus on 2010-04-20
Hi,
I just did do a search on this subject but couldn't really find what I was looking for.
At the moment I have a perfectly running system and I would like to make a copy / back-up from that so in case somethings happens I can always place it back as if nothings happened.
How do I do that? What programs do I use? Who can help me with that?

---

### Post by foxmulder881 on 2010-04-20
Install partimage.

```
sudo apt-get install partimage
```

Note: Although, from what I can see at the moment, it doesn't yet support ext4 partitions.

---

### Post by DeMus on 2010-04-20
> **foxmulder881 said:**
> Install partimage.

```
sudo apt-get install partimage
```

Note: Although, from what I can see at the moment, it doesn't yet support ext4 partitions.

Thank you for your answer. I do use Ext4 partitions all over so I need a back-up program for that.
Isn't it possible to just copy (cp) everything or doesn't that work? Before I try I want to know absolutely sure it will work, especially the way to restore the files and folders.

Who else can help me?

---

### Post by l4zy on 2010-04-20
Read about rsync. It's really nice tool to make backups.

like if you want to backup everything in your home. This script backups your home and when you run it again, it deletes those from backup which you have deleted.

rsync --verbose  --progress --stats --compress --recursive --times --perms --links --delete /home/* /mnt/backup/home/

but this is just an example.

---

### Post by d3v1150m471c on 2010-04-20
just use the rsync command.

---

### Post by Serpher on 2010-04-20
To backup assuming you're partition one on sda:

```
$dd if=/dev/sda1 of=backup.img
$gzip  backup.img
```

Make sure you back up this file on some kind of external media, it might be pretty large.


To restore on a live disc, mount the partition with your image on it, format the partition you want to restore with Disk Manager gparted or '$fdisk /dev/sda', and execute:

```
$gunzip /media/<Filesystem>/<Wherever backup.img is>
$dd if=/media/<Filesystem>/<Wherever backup.img is>
```


You should probably test the partition before trying this with (assuming it's ext4):

```
$mount -o loop -t ext4 ~/media/<Filesystem>/<Wherever backup.img is> ~/<Any blank folder>
```

---

### Post by DeMus on 2010-04-20
> **Serpher said:**
> To backup assuming you're partition one on sda:

```
$dd if=/dev/sda1 of=backup.img
$gzip  backup.img
```

Make sure you back up this file on some kind of external media, it might be pretty large.


To restore on a live disc, mount the partition with your image on it, format the partition you want to restore with Disk Manager gparted or '$fdisk /dev/sda', and execute:

```
$gunzip /media/<Filesystem>/<Wherever backup.img is>
$dd if=/media/<Filesystem>/<Wherever backup.img is>
```


You should probably test the partition before trying this with (assuming it's ext4):

```
$mount -o loop -t ext4 ~/media/<Filesystem>/<Wherever backup.img is> ~/<Any blank folder>
```

Thank you for your answer. I presume I have to do this from a live CD, right? Otherwise the running system will be overwritten.
Also another question about the restore process:
You write:
```
$gunzip /media/<Filesystem>/<Wherever backup.img is>
$dd if=/media/<Filesystem>/<Wherever backup.img is>
```
Don't you have to specify an output file/folder name like you did when backing up the system?

---

### Post by DeMus on 2010-04-20
> **l4zy said:**
> Read about rsync. It's really nice tool to make backups.

like if you want to backup everything in your home. This script backups your home and when you run it again, it deletes those from backup which you have deleted.

rsync --verbose  --progress --stats --compress --recursive --times --perms --links --delete /home/* /mnt/backup/home/

but this is just an example.

Yes, I do use rsync for my weekly back-ups, never thought of also use it for a system back-up.
Thanks for the tip.

Thanks also to d3v1150m471c.

---

### Post by Mark Phelps on 2010-04-20
You might also want to look into Clonezilla.  Although it's intended to be run from its own LiveCD, they have a docs page that shows how to install it into your Linux partition, and have it selectable from the GRUB menu.  You still have to reboot to run it, but you don't have to mess with carrying around a CD.

---

### Post by donsy on 2010-04-20
I've never used it but can't you copy a partition with gparted?

---

