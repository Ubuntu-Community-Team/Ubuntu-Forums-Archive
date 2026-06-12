---
title: "PYSDM doesn't show my windows partition"
date: 2010-08-31
forum: General Help
---

### Post by schwabdale on 2010-08-31
Hello,
I've done this many times before, but am having problems now. 

I want to auto mount my ntfs partition using pysdm. However, it does not see it. 
When I do an fdisk -l it shows up. I can access the partition through my home folder... it just doesn't show up in pysdm. I have already tried to reinstall the program. 

Any ideas?

---

### Post by Morbius1 on 2010-08-31
Is your question specifically about pysdm, or do you want to automount your ntfs partition.

If it's the latter then please post the output of the following commands and specify what ntfs partition you want to automount:

```
sudo blkid -c /dev/null
``````
mount
``````
cat /etc/fstab
```

---

### Post by schwabdale on 2010-08-31
[sudo] password for secure: 
/dev/sda1: LABEL="RECOVERY" UUID="5A08FF7B08FF550B" TYPE="ntfs" 
/dev/sda2: UUID="6496DA8E96DA5FDA" TYPE="ntfs" 
/dev/sda5: UUID="55d98896-5cd8-4d06-be89-4948694c3316" TYPE="ext4" 
/dev/sda6: UUID="53dcfb53-9f4a-444e-ad00-c3fd06b7c979" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 


/dev/sda1: LABEL="RECOVERY" UUID="5A08FF7B08FF550B" TYPE="ntfs" 
/dev/sda2: UUID="6496DA8E96DA5FDA" TYPE="ntfs" 
/dev/sda5: UUID="55d98896-5cd8-4d06-be89-4948694c3316" TYPE="ext4" 
/dev/sda6: UUID="53dcfb53-9f4a-444e-ad00-c3fd06b7c979" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
secure@secure-desktop:~$ ^C
secure@secure-desktop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/secure/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=secure)


cat /etc/fstab

cat /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=55d98896-5cd8-4d06-be89-4948694c3316 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=53dcfb53-9f4a-444e-ad00-c3fd06b7c979 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=996aaa77-c948-4d2e-aebe-e48fcdbbc6b9 none            swap    sw



I want to automount sda2

---

### Post by Morbius1 on 2010-08-31
>  /dev/sda2: UUID="6496DA8E96DA5FDA" TYPE="ntfs" **1st: Decide on where you want the mountpoint and then create one:**
```
sudo mkdir /media/DiskA2
```It can be anywhere as you already know. Mountpoints in /media or in your own home folder will produce desktop icons and show up under places. Mountpoints in /mnt or anywhere else do not.

**2nd: Open fstab as root:**
```
gksu gedit /etc/fstab
```**3rd: Add a line to the end of fstab to mount the partition:**
```
/dev/sda2 /media/DiskA2 ntfs defaults,umask=000,nls=utf8 0 0 
```**4th: Save fstab, exit gedit, and back in the terminal mount the new fstab entry:**
```
sudo mount -a
```It should mount the partition to /media/DiskA2 without rebooting.

---

### Post by schwabdale on 2010-08-31
That did it! Thanks so much!

---

### Post by megerdin on 2012-05-01
Thanks really helpfull

---

### Post by oldos2er on 2012-05-01
Old thread closed.

---

