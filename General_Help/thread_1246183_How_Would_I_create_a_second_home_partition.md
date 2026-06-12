---
title: "How Would I create a second home partition"
date: 2009-08-21
forum: General Help
---

### Post by dave r on 2009-08-21
I go about setting a second home partition, run two home partitions? And could I allocate the second home partition to one user? I know how to create the partition but how would I set the new partition to one user? would I have to edit Grub?

---

### Post by cariboo on 2009-08-21
> **dave r said:**
> I go about setting a second home partition, run two home partitions? And could I allocate the second home partition to one user? I know how to create the partition but how would I set the new partition to one user? would I have to edit Grub?

Why do you want to setup a second home partition? It will override the home partition you already have setup.

If you want to setup another user, their home directory will be located in /home also.

There is no need to set anything up in grub, as automatically mounting partitions is handled by /etc/fstab, this is what fstab on this computer looks like:

```
cat /etc/fstab
# Pluggable devices are handled by uDev, they are not in fstab
/dev/hdb1 / ext3 defaults,noatime 1 1
/dev/hdb2 swap swap sw,pri=1 0 0
proc /proc proc defaults 0 0
devpts /dev/pts devpts mode=0622 0 0
**/dev/hdb3 /home ext3 defaults,noatime 1 2**
# Dynamic entries below
/dev/hda1 /mnt/hda1 ntfs-3g noauto,users,gid=users,dmask=002,fmask=113,relatime 0 0
/dev/sda1 /mnt/sda1 ext4 noauto,users,exec,relatime 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/hdc /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
```

I have bolded the entry for my home partition. Yours may look different, because as of Ubuntu v8.10  UUID is used to identify the partition instead of the device number.

---

### Post by dave r on 2009-08-21
thanks cariboo907, it was just an idea I had, I've got a better idea how it all works now.

---

