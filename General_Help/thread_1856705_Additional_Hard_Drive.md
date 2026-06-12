---
title: "Additional Hard Drive"
date: 2011-10-08
forum: General Help
---

### Post by dmillerct on 2011-10-08
I have a 1TB drive that is used to keep photos, movies, documents, etc. This is currently mounted as:

/dev/sdb


My user account has no rights over the drive and I am therefore unable to add files to the drive or subfolders. How can I take ownership of this drive and set permissions on the sub directories to grant me write access?

---

### Post by WorMzy on 2011-10-08
> **dmillerct said:**
> I have a 1TB drive that is used to keep photos, movies, documents, etc. This is currently mounted as:

/dev/sdb

No, it's not.

/dev/ lists device nodes, not mount points. Also, (unless this is a very rare case) that is the disk itself, not the partition containing your photos and such. You need to mount the partition to be able to access the files on it.

Now, assuming the disk only has one partition on it, and assuming that partition is a primary partition, you can mount it by running:

```
udisks --mount /dev/sdb1
```

or, failing that:

```
sudo mount /dev/sdb1 /mnt
```

Depending on the filesystem the partition uses, you may find that you are unable to edit the files in any way after mounting with the "sudo mount" command. If you find this to be the case, unmount the partition with the following command:

```
sudo umount /mnt
```

then remount the partition with the following command:

```
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdb1 /mnt
```

If you want the partition to be mounted every time you boot up, add it to your /etc/fstab file. You can follow this tutorial if the filesystem is NTFS or FAT: [http://ubuntuforums.org/showthread.php?t=1604251]("http://ubuntuforums.org/showthread.php?t=1604251"), otherwise post the output of:

```
sudo blkid -c /dev/null
```

here, and we'll tell you what you need to put.


EDIT: Oh, and I nearly forgot the simplest way of mounting. Open up nautilus (the file manager) and look at the bottom on the left-hand side; you should see a list of partitions that Ubuntu can identify. Simply click one of them to automatically mount it and open it. It will remain mounted until you unmount it, or restart your machine.

---

### Post by dmillerct on 2011-10-08
You are correct. it was /dev/sdb1 or /media/sdb1 once mounted.

I unmounted and mounted using the following command as you suggested: ```
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdb1
```

The partition mounted but I am still unable to create / add files.

---

### Post by WorMzy on 2011-10-08
Yeah, you should have gotten an error with that command, something like "can't find /dev/sdd3 in /etc/fstab or /etc/mtab". I forgot the last argument when I typed that, the mount point.

Try:```
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdb1 /mnt
```

EDIT: Wait, it mounted without you specifying a mount point? Maybe Ubuntu is shipping with an augmented version of mount these days. Since it mounted without error, please post the output of

```
mount
```

---

### Post by dmillerct on 2011-10-08
here is the output of mount: (it looks like this is an NTFS partition)

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/dan/.Private on /home/dan type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=78ff3ac965061c1d,ecryptfs_fnek_sig=c780ed3637f1d533)
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)
/dev/sdb1 on /media/sdb1 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

---

### Post by WorMzy on 2011-10-08
> **dmillerct said:**
> here is the output of mount: (it looks like this is an NTFS partition)

You mean you didn't know? @_@

Anyway, it looks like you didn't successfully unmount it before you tried to remount it (so the mount command "succeeded", but didn't actually do anything).

Remember to unmount it first; that command I gave you before to unmount it assumed that you had mounted it to /mnt, not /media/sdb1. So first unmount it with:

```
sudo umount /dev/sdb1
```

then mount it with:

```
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdb1 /mnt
```

---

### Post by dmillerct on 2011-10-08
```
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdb1 /mnt
``` did not work

```
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdb1
``` mounted the drive but again, I still dont have permission to create / modify files.

I think I just might copy files over then format it ext4.

---

### Post by WorMzy on 2011-10-08
> **dmillerct said:**
> ```
sudo mount -o uid=1000,gid=1000,umask=022 /dev/sdb1 /mnt
``` did not work

Did you get a specific error?

---

### Post by dmillerct on 2011-10-08
> **WorMzy said:**
> Did you get a specific error?

No, none. It just did not mount the partition.

---

### Post by WorMzy on 2011-10-08
That's bizarre.

Well, if you do reformat the partition as ext4, be aware that you won't be able to use it on Windows operating systems. It will only be accessible from Linux operating systems.

(There are drivers available that will let you read/write to ext# partitions from Windows, but personally, I wouldn't touch them.)

---

### Post by dmillerct on 2011-10-08
You think fat32 would be better?

---

### Post by WorMzy on 2011-10-08
No, worse. FAT32 is in the same boat as NTFS, only FAT32 is outdated and depreciated.

---

### Post by dmillerct on 2011-10-08
OK, I will stick with ext4. these files are primarily accessed through samba shares anyway. thanks for your help.

---

