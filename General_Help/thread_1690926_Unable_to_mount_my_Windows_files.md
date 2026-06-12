---
title: "Unable to mount my Windows files"
date: 2011-02-19
forum: General Help
---

### Post by Levakama on 2011-02-19
Hello, I used this guide : [http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/](http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/) 

It worked normally but I found out I mounted the wrong drive, /dev/sda1 instead of /dev/sda2 .
So after a restart the windrive directory was empty so I wanted to retry the guide with the correct the drive but whenever I try that  it says Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

The windows installation is WIndows 7 and Ubuntu is Maverick if it helps.

---

### Post by Morbius1 on 2011-02-19
Please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by Levakama on 2011-02-19
> **Morbius1 said:**
> Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```
```
/dev/loop0: UUID="93128bac-f6f6-475e-91c6-2e499f0c2dc3" TYPE="ext4" 
/dev/sda1: LABEL="RezervovM-CM-!no systM-CM-)mem" UUID="7E56C51356C4CCD9" TYPE="ntfs" 
/dev/sda2: UUID="D6EEC6DFEEC6B751" TYPE="ntfs" 

```


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       
``````
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ladislav/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ladislav)

```

---

### Post by Morbius1 on 2011-02-19
Sorry, this is not a regular install of Ubuntu. It looks like a Wubi install - install within Windows. I have zero experience in Wubi but I think that the Windows files you seek already are mounted in File System > Host.

---

### Post by Levakama on 2011-02-19
> **Morbius1 said:**
> Sorry, this is not a regular install of Ubuntu. It looks like a Wubi install - install within Windows. I have zero experience in Wubi but I think that the Windows files you seek already are mounted in File System > Host.
Yes,that was it,thanks you.

---

