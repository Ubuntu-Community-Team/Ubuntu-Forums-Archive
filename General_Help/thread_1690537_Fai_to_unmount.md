---
title: "Fai to unmount"
date: 2011-02-18
forum: General Help
---

### Post by d_darlac on 2011-02-18
there are some drives in my system that appear to be always mounted (were at some point) that I cannot get rid of -
i checked fstab, and do not appear there - 
2 are related with the use of truecrypt, and 1 is from an exernal HD

I use Maverick 10.10 x64
any help is appreciated!

---

### Post by ajgreeny on 2011-02-18
In terminal run the command ```
mount
``` and look to see if you can find the disks/partitions listed there; they should show up probably at the bottom of the list, which should look something like:-
```
**/dev/sda1 on / type ext4 (rw,errors=remount-ro)**
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
**/dev/sda2 on /home type ext4 (rw)**
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/*user*/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=*user*)
[B]/dev/sdb1 on /media/Maverick type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3 on /media/Mint10 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb2 on /media/UNR type ext4 (rw,nosuid,nodev,uhelper=udisks)[/B]
```
The first line is your the partition, then there are several virtual partitions, then in my case my home partition, two more virtual system mounts, and finally three partitions I mounted simply to show how they will look for you.  To unmount these partitions you would use the command ```
sudo umount /media/*mountpoint*
```

---

### Post by d_darlac on 2011-02-18
thanks, but doesn't seem to work:
here the mount command output:
dimitris@dimitris:~$ mount
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
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda5 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dimitris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dimitris)

and attached is an image of mounted volumes - 
the last 3 (dm-0, mpoint, truecrypt1) are empty, and cannot get rid of them (thy do not appear on the top list)

thanks

---

### Post by d_darlac on 2011-02-21
I found in another trend how to solve the problem:
umount, to unmount any folder
and then
rmdir to remove it!

---

