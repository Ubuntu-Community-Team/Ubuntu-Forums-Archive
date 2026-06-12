---
title: "Partiton access problem"
date: 2010-12-24
forum: General Help
---

### Post by zainlodhi on 2010-12-24
I have two operating system Windows 7 and Ubuntu installed on my PC. I have three partitions out of which two partitions are NTFS file system. How can I change my working directory to these NTFS partitions using command line interface.

---

### Post by oldfred on 2010-12-24
It is just cd
cd /usr/local/fred/shared

I mount my shared NTFS into the above path and then link folders into /home. You can directly mount into your /home if that is easier.

You need to create a mount point and permanently mount your partitions with fstab. I would suggest only mounting your win7 read-only so you do not accidentally delete or move something important to windows, as with Ubuntu you see all the hidden system files that windows protects you from.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by zainlodhi on 2010-12-24
how to mount shared NTFS on above path.

---

### Post by oldfred on 2010-12-24
# are comments, 
#These are commands I run, but I have them in a script since I add many system partitions to test installs and want to moutn all my data

```
mkdir /mnt/cdrive
mkdir /mnt/shared

To see your UUID and partitions:
sudo blkid
sudo fdisk -l
cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
#Edit fstab first, with partitions & UUIDs of NTFS partitions
# Entry for /dev/sda1 :"
UUID=04B05B70B05B6768          /mnt/cdrive  ntfs-3g      defaults           0  0  
# Entry for /dev/sdc2 :"
UUID=44332FD360AA9657         /mnt/shared  ntfs-3g      defaults            0  0

#any time you edit fstab run this to verify everything is correct. Its ok if it does not give any messages.
sudo mount -a
# from home so default location will be /home/fred
ln -s /mnt/shared

```

---

