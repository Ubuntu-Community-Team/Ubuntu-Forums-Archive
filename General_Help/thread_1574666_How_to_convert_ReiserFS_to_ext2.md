---
title: "How to convert ReiserFS to ext2?"
date: 2010-09-14
forum: General Help
---

### Post by cocopeanut on 2010-09-14
I have a installation of Ubuntu on a flash drive that I just finished updating, etc. I noticed that it ran surprisingly slow during all my updates and software installations. I looked into it further and found out that for Flash Drive installations, it is recommended to use ext2 due to it's speed and lack of journaling (to limit the amount of writes to the disk).
 
So my question is this.......
 
I REALLY don't want to spend all the time and effort I have just spentt on reinstalling from scratch! I'd like to convert my partition filesystem from ReiserFS to ext2. How can I do this?
 
If it's not possible...... Can I backup all the information, do a new installation using the LiveCD, and restore the backup? What program can I use, and which directories do I need to backup?
 
Thank you!!
 
-Oscar Mansour
(a semi-intermediate linux user :-)

---

### Post by srs5694 on 2010-09-14
AFAIK, there's no way to convert from ReiserFS to ext2fs in place; you'll have to back up, create a fresh ext2 filesystem, and restore. You'll need to back up *everything* on the partition(s) that use ReiserFS. Personally, I'd use tar, with a command like this from a boot CD:

```

sudo tar cvpzf /dir/to/backup/backup.tgz /dir/to/source

```Change /dir/to/backup and /dir/to/source to suitable directories, of course. You can then unmount /dir/to/source, use mke2fs on it, re-mount it, and restore the backup:

```

cd /
sudo tar xvpzf /dir/to/backup/backup.tgz

```Do this separately for each ReiserFS partition. When you're done, mount the root partition at /dir/to/backup and edit /dir/to/backup/etc/fstab. You'll need to change the UUID value for the root filesystem. Use blkid to identify the new UUID, as in "sudo blkid /dev/sdb#", where "/dev/sdb#" is the device ID for the flash drive's root partition. (It might not even be on /dev/sdb.) It's conceivable you'll need to tweak your GRUB configuration, too, to have it load an ext2/3/4 module rather than a ReiserFS module. Peruse /dir/to/backup/boot/grub/grub.cfg (or the equivalent in a separate /boot partition, if you've used one) for references to ReiserFS and change them, if necessary.

Edit: Oh, when you're editing /etc/fstab, be sure to change the filesystem type code from reiserfs to ext2, as well!

---

