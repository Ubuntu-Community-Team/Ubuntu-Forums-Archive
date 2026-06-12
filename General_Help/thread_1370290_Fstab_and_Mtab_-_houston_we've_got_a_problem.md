---
title: "Fstab and Mtab - houston we've got a problem"
date: 2010-01-02
forum: General Help
---

### Post by linus022 on 2010-01-02
I have problem with fstab or mtab (or both) I made two partitions (/disk/media and /disk/media-1) and i wanted to mount them automaticly. So i edited fstab. I also found i internet command "sudo rm /etc/fstab which i used. And it was mistake. Now i tried to rebuild fstab with my own bare hands. First my two partitions weren't working but now don't work only partition /home so i must login onto root account.

So my partitions are:
```
/dev/sda1  ext3  /
/dev/sda2  ext3 /home (NOT WORKING)
/dev/sda3  none swap
/dev/sda5  ntfs  /media/disk
/dev/sda6  ext2 /media/disk-1
```And also: this partiotion /home isn't mount able from e.g computer folder in ubuntu. I tried and I got this 
mount point cannot contain following characters newline, G_dir_separator (usually /)
Logs from fstab:
     ```
Kod:
     # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# dev/sda1 UUID=cdd9a0be-a8c6-430a-a4f4-037da29c45d0 / ext3 relatime,errors=remount-ro 0 1

# dev/sda2 UUID=aa880b52-62e9-4ee7-9240-151fc5f20306 /home ext3 defaults 0 2

# dev/sda3 UUID=07b3abad-6bb4-4472-8e24-74fe814b9a54 none swap defaults 0 0

# dev/sda5 UUID=1F6326131D425DE8 /media/disk ntfs defaults 0 2

# dev/sda6 UUID=92db8494-8b2d-4fde-a724-e36453f3537b /media/disk-1 ext2 defaults 0 2 
```logs from mtab (problably wrong ones)
```
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-26-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
/dev/sda5 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda6 /media/disk-1 ext2 rw,nosuid,nodev,uhelper=hal 0 0
```Can someone help me with that? btw - my user nickname in linux is linus and computer name - HP. And gparted says that two first partitions (/ and /home) doesn't have mount points. How i can repair it?

Can someone here help me?

---

### Post by PeEllAvaj on 2010-01-02
The first thing I notice when I look at your fstab is that each of the lines are commented out.  Was that intentional for some reason?  I would think your fstab should look like this, with the UUID being the start of each line:

> #
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# dev/sda1 
UUID=cdd9a0be-a8c6-430a-a4f4-037da29c45d0 / ext3 relatime,errors=remount-ro 0 1

# dev/sda2 
UUID=aa880b52-62e9-4ee7-9240-151fc5f20306 /home ext3 defaults 0 2

# dev/sda3 
UUID=07b3abad-6bb4-4472-8e24-74fe814b9a54 none swap sw 0 0

# dev/sda5 
UUID=1F6326131D425DE8 /media/disk ntfs defaults 0 2

# dev/sda6 
UUID=92db8494-8b2d-4fde-a724-e36453f3537b /media/disk-1 ext2 defaults 0 2

---

### Post by linus022 on 2010-01-02
Now that's working, problem sloved. Thanks you all!

---

