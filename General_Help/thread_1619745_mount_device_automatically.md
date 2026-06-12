---
title: "mount device automatically"
date: 2010-11-12
forum: General Help
---

### Post by slwx on 2010-11-12
Hi,
I was wondering if I can mount my second hard drive (/dev/sda4/) automatically on startup?  
Now I have to enter my password every time.

Thanks,
Mathias

---

### Post by TeoBigusGeekus on 2010-11-12
Mount it and post us the output of
```
blkid
```
and
```
mount
```

---

### Post by Verbeck on 2010-11-12
you'll need to edit your /etc/fstab and add a new entry for that partition

post the output of the following while the device is connected
```
sudo blkid
```

---

### Post by slwx on 2010-11-14
Hi, 
sory for late reply.

mathias@mathias:~$ sudo blkid
[sudo] password for mathias: 
/dev/sda1: UUID="6444406CE49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="EAEC1FF5EC1FBB31" LABEL="ACER" TYPE="ntfs" 
/dev/sda4: UUID="D60C17D00C17AB0F" LABEL="Muziek en Films" TYPE="ntfs" 
/dev/sdb1: UUID="518b5ed0-d261-4181-b205-b77f40334f6d" TYPE="ext4" 
/dev/sdb2: LABEL="swap" UUID="81627041-fe2d-4d68-aa54-b0d7e0d64506" TYPE="swap" 

mathias@mathias:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mathias/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mathias)
/dev/sda4 on /media/Muziek en Films type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

what now?
thanks Mathias

---

### Post by Verbeck on 2010-11-14
type the following in a terminal window
```

sudo umount /dev/sda4
sudo mkdir /media/Muziek-en-Films
sudo chown -R **username**:**usergroup **/media/Muziek-en-Films
sudo gedit /etc/fstab
```when the gedit window pops up, enter the following in a new line
```
UUID=D60C17D00C17AB0F /media/Muziek-en-Films ntfs defaults 0 0
```after that, run sudo mount -a

---

### Post by slwx on 2010-11-14
worked fine!

thanks!

---

