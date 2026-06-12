---
title: "My experience downgrading ext4 file systems"
date: 2010-01-01
forum: General Help
---

### Post by ilerdl on 2010-01-01
This post is not to ask for help, but rather to document my recent effort to downgrade my ext4 file systems to ext3 file systems.  I don't know if it'll help anyone, but here it is anyway, fwiw.

I am running ubuntu 9.10 on an older Dell GX-270, and had formatted my partitions with ext4 file systems.  I began to notice partimage wasn't backing up my ext4 file systems and I decided to downgrade to ext3 file systems.

My system has one 160GB drive and one 500GB drive.  I also have an external usb2 500GB drive.

/home is on the internal 500GB drive.  To convert it, I mounted an ntfs file system on the external drive, created a container file, put a file system on it, and mounted the container as a linux file system.

mkdir /mnt/backup && ntfs-3g /dev/sdc1 /mnt/backup
dd if=/dev/zero of=/mnt/backup/lfs bs=1G count=100
mkfs.ext2 -F /mnt/backup/lfs
mkdir /mnt/container && mount -t ext2 -o loop /mnt/backup/lfs /mnt/container

The backup was done done via rsync.  rsync makes things really easy.  It understands uids, gids, file permissions, and all kinds of links.  That's one reason I created the container file on my external drive.  NTFS doesn't understand uids gids, linux file permissions, or linux style links.

mkdir /mnt/h && mount -t ext4 /dev/sda7 /mnt/h
rsync -av /mnt/h /mnt/container

Then an ext3 file system was put on the partition.

umount /mnt/h
mkfs.ext3 /dev/sda7

The UUID of the newly formatted partition was obtained from blkid

blkid /dev/sda7

And the UUID was changed in the root file system, along with the file system type.

mkdir /mnt/r && mount -t ext4 /dev/sda6 /mnt/r
vi /mnt/r/etc/fstab

The old UUID was deleted, the new one inserted, and the file system type changed from ext4 to ext3.

Then the new ext3 file system was mounted and the information restored by rsync.

mount -t ext3 /dev/sda7 /mnt/h
rsync -av /mnt/container/h /mnt

Then the CD was removed, and the system rebooted to ensure a clean and error-free boot.

This same procedure was repeated for:
 sdb6 - /tmp
 sdb7 - /var
 sdb8 - /opt

Each file system conversion got a clean boot.

The root file system was done the same way, except that once done, the system did not boot.  Then I remembered I had forgotten to convert the root file system UUIDs in /boot/grub/grub.cfg.  Once that was done, the system booted cleanly with no errors, and all file systems had been converted from ext4 down to ext3.

My file system downgrades never touched the MBR or the /boot partition, which was already at ext2.

Cordially,


Dave

---

### Post by birne on 2010-08-30
Thanks, Dave, for this great howto. Your approach worked perfectly for me!

Use case: 
I needed to downgrade from ext4 to ext3 after a clean install of Lucid, following a hd breakdown. Acronis true image recovery disk (version 10) was unable to mount the new partitions, so i could not restore any backup files to the new hard disk. The reason was that the new hd had been formatted with ext4, a format Acronis (as of v. 10) does not support. After the downgrade everything worked smoothly.

---

