---
title: "fstab entry"
date: 2011-07-24
forum: General Help
---

### Post by chrisrodgers on 2011-07-24
Hi! I have a disk that is formatted as NTFS (from Windows 7 - dual boot with Ubuntu Studio).  This is not a boot disk, just an extra disk for data.  I would like it to be available to both OS's.  In Ubuntu, I went to System -> Administration -> Disk Utility and saw the disk.  I clicked on the volume name and clicked Mount.  I would like this always mounted when I restart Ubuntu.  It was mounted as /media/Data2 (/dev/sdc5).

What is the best/preferred way to format the entry in /etc/fstab?  In a shell, I see the following:

```
chris@dumbo-PC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b6523e94-368e-45bf-a40d-cff8a7ec7623 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fd61c860-1b6c-4c4c-bc88-17bbfccdb038 none            swap    sw              0       0
chris@dumbo-PC:~$ 
chris@dumbo-PC:~$ 
chris@dumbo-PC:~$ mount
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
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
/dev/sdb3 on /media/Data1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5 on /media/Data2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
chris@dumbo-PC:~$ 
chris@dumbo-PC:~$ 
chris@dumbo-PC:~$ sudo blkid
/dev/sda1: UUID="b6523e94-368e-45bf-a40d-cff8a7ec7623" TYPE="ext4" 
/dev/sda5: UUID="fd61c860-1b6c-4c4c-bc88-17bbfccdb038" TYPE="swap" 
/dev/sdb1: LABEL="RECOVERY" UUID="01CC498F953F3400" TYPE="ntfs" 
/dev/sdb2: LABEL="Win7" UUID="01CC498FA38D5000" TYPE="ntfs" 
/dev/sdb3: LABEL="Data1" UUID="01CC498F62953B80" TYPE="ntfs" 
/dev/sdc5: LABEL="Data2" UUID="01CC498FE4856480" TYPE="ntfs" 
/dev/sdd: TYPE="isw_raid_member" 
/dev/sde: TYPE="isw_raid_member" 
/dev/mapper/isw_cadhgeighb_Volume0p1: LABEL="ARCH01" UUID="7E0EC3BF0EC36F29" TYPE="ntfs" 
chris@dumbo-PC:~$ 

```

---

### Post by Morbius1 on 2011-07-24
[1] Unmount the currently mounted partition:
```
sudo umount /media/Data2
```[2] Create a permanent mount point:
```
sudo mkdir /media/Data2
```[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line to the end of fstab:
```
UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
```[5] Save fstab, exit gedit and back in the terminal run the following command which will test for errors and mount the partition without a reboot:
```
sudo mount -a
```

---

### Post by flemur13013 on 2011-07-24
I have a shared, non-booting NTFS partition created by Win7.  
It's labeled 'NTFS' and mounted at /ntfs 

```
sudo mkdir /ntfs
```

Add this line to /etc/fstab (most people seem to have more interesting parameters, but this simple line has always worked fine for me) :

```
UUID=yourUUID    /ntfs   ntfs    defaults   0   2
```

Reboot or do the umount / mount thing.

---

### Post by chrisrodgers on 2011-07-24
> **Morbius1 said:**
> [4] Add the following line to the end of fstab:
```
UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
```

Thanks, Morbius!  Question for you, what do the extra parameters of UID and umask do?  How does that affect the use of the volume?  Thanks for helping me out!

---

### Post by WorMzy on 2011-07-24
UID=1000 = the first user you create (when you installed Ubuntu)
umask=000 = permissions of 777 = Allow everyone to read, write and execute files on the partition.

Amend these two variables are required. umask operates the opposite way that chmod does. Read this for more info: [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

### Post by Morbius1 on 2011-07-25
What WorMzy said :).

Here's the reason I added those parameters.

uid=1000 will make you the owner of the partition and I added it because:

* It makes it simpler to share it across the network using Samba if you own it.
* It gives you the ability to send something to the trash. Without it root owns the partition and if you try to send something to the trash you will get an error message because it's trying to send it to root's trash and you aren't root.

umask=000 is really unnecessary since it's in the "defaults" parameter. I like to add it explicitly so that I know what I've set it to and because I never know if the "defaults" will change with an update without anyone telling me.

---

