---
title: "How to change the owner/permission of a hard disk drive?"
date: 2012-03-04
forum: General Help
---

### Post by lonekingc4 on 2012-03-04
Hi. I am using Ubuntu 11.10 in my Netbook. When installing Ubuntu, I created 3 partitions: one for the Ubuntu itself, one as a swap area and the other as a normal hard disk drive. But now I cannot create folders or anything in the hard disk drive. I right clicked and selected Properties-->Permissions and it said that the owner is "root". How can I change the owner to my account? If not, how can I change the permissions etc? Thanks.

---

### Post by oldfred on 2012-03-04
What format did you make for the data partition.

If NTFS the owner will be root as NTFS does not support ownership and permissions by file. But when you mount it you give yourself all your rights on the entire partition.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by lonekingc4 on 2012-03-04
> **oldfred said:**
> What format did you make for the data partition.

If NTFS the owner will be root as NTFS does not support ownership and permissions by file. But when you mount it you give yourself all your rights on the entire partition.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)


The file system is EXT4, as same as the drive where Ubuntu itself is installed in :)
By the way, will this work: "sudo chown lonekingc4 /dev/sda6"

---

### Post by mcduck on 2012-03-04
> **lonekingc4 said:**
> The file system is EXT4, as same as the drive where Ubuntu itself is installed in :)
By the way, will this work: "sudo chown lonekingc4 /dev/sda6"

No, you definitely should not chown the device! That's supposed to be owned by the system, and changing the ownership would most likely just break things.

But chown on the *mountpoint* or any directory inside the filesystem will work just fine.

---

### Post by 0011235813 on 2012-03-04
If you need to just view something quickly you can use:
```
gksu nautilus
```
but otherwise, you can use:
```
chown -R <username> <location>
```
chown being change owner, -R being recursive (i.e make all sub-directories as well), your username is the user you want to change it to, and location is where the file or directory is located (probably something like /dev/sdba4). 
Note: I think you have to run it as root for it to work, in which case use:
```
sudo -i
```
to obtain a root shell.

PS: These things are always a pain, the developers must find a way to make graphic integration in nautilus so you can open root folders with authentication and easily change permissions.

---

### Post by oldfred on 2012-03-04
You can do this, but if it is a partition on your internal drive you should add it to fstab, so everytime your reboot it is automatically mounted.

sudo mkdir /mnt/data
sudo chmod 766 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda6 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

# find UUID for sda6 and use that in place of example below:
sudo blkid
# backup fstab
sudo cp /etc/fstab /etc/fstab.backup
# edit fstab
gksudo gedit /etc/fstab
# remount with new fstab, if no errors it just returns
sudo mount -a


# Entry for /dev/sda6 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /mnt/data    ext4         relatime               0  2

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

Link folders into /home from /mnt/data
Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by lonekingc4 on 2012-03-04
> **mcduck said:**
> No, you definitely should not chown the device! That's supposed to be owned by the system, and changing the ownership would most likely just break things.

But chown on the *mountpoint* or any directory inside the filesystem will work just fine.

Thanks a lot. I just created a directory inside that drive using "sudo mkdir" and then changed the owner and group of that directory from root to my account using chown. That did the trick! Now I can just use that directory to store my files :D

Thanks everyone for your answers :)

Cheers.

---

### Post by 0011235813 on 2012-03-04
> **lonekingc4 said:**
> Thanks a lot. I just created a directory inside that drive using "sudo mkdir" and then changed the owner and group of that directory from root to my account using chown. That did the trick! Now I can just use that directory to store my files :D

Thanks everyone for your answers :)

Cheers.

Did you use the recurring argument? Remember that without it, all sub-directories created there will **not** belong to you.

---

### Post by bab1 on 2012-03-04
> **0011235813 said:**
> Did you use the recurring argument? Remember that without it, all sub-directories created there will **not** belong to you.
Using the recurring argument allows you to change permissions of files and directories that already exist.  The prevailing permissions and umask determine what future files and directories can be created and what their permissions will be.

---

### Post by 0011235813 on 2012-03-04
> **bab1 said:**
> Using the recurring argument allows you to change permissions of files and directories that already exist.  The prevailing permissions and umask determine what future files and directories can be created and what their permissions will be.

I was just saying in case the OP already had put some files and directories there.

---

