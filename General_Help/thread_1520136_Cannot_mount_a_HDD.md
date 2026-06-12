---
title: "Cannot mount a HDD"
date: 2010-06-29
forum: General Help
---

### Post by nemiux on 2010-06-29
When I try to mount my ntfs hdd partition /deb/sdb3 that is called 'Stambus failai' I get this error displayed in the thumblain.
This is my fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc                  proc  defaults                0  0  
/host/ubuntu/disks/root.disk  /                      ext3  loop,errors=remount-ro  0  1  
/host/ubuntu/disks/boot       /boot                  none  bind                    0  0  
/host/ubuntu/disks/swap.disk  none                   swap  loop,sw                 0  0  
/dev/sdb3                     /media/Stambus failai  ntfs  defaults                0  0  
```
And in case you might need it this is my mtab: ```
/host/ubuntu/disks/root.disk / ext3 rw,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
/dev/sdb1 /host fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-19-generic/volatile tmpfs rw,mode=755 0 0
/host/ubuntu/disks/boot /boot none rw,bind 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/nemiux/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=nemiux 0 0
/dev/sda5 /media/Senas\040mano fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
```

Thanks
Edit: I want to open the HDD by going to Places and clicking on it, not by writing mount commands.

---

### Post by justleen on 2010-06-29
there is a space in there... fstab will see failai as a column and cant mount it as a FStype Failai

---

### Post by Leppie on 2010-06-29
try modifying the fstab entry like this:
```
/dev/sdb3                     /media/Stambus\ failai  ntfs  defaults                0  0
```

---

### Post by nemiux on 2010-06-29
After doing that I get this error displayed in the thumblain.

---

### Post by warfacegod on 2010-06-29
> **Leppie said:**
> try modifying the fstab entry like this:
```
/dev/sdb3                     /media/Stambus\ failai  ntfs  defaults                0  0
```

Doesn't this need an UUID? And shouldn't "Stambus\ failai" be "Stambus\failai"? (Without the actual space.)

Just guessing here.

---

### Post by nemiux on 2010-06-29
I think it helped, but i guess there's one more problem. Again the thumblain :)

---

### Post by dino99 on 2010-06-29
i dont like headache so i use mountmanager, i'm too lazy to use anything else

---

### Post by warfacegod on 2010-06-29
> **nemiux said:**
> I think it helped, but i guess there's one more problem. Again the thumblain :)


From: [http://www.tuxera.com/community/ntfs-3g-faq/](http://www.tuxera.com/community/ntfs-3g-faq/)

```
Why do I get “fusermount: option blkdev is privileged” error?

Unprivileged block device mounts work only if all the below requirements are met:

   1. ntfs-3g is compiled with integrated FUSE support
   2. the ntfs-3g binary is at least version 1.2506
   3. the ntfs-3g binary is set to setuid-root
   4. the user has access right to the volume
   5. the user has access right to the mount point

The root user can make an ntfs-3g binary setuid-root as shown below
chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g) In such case the driver will also be able

    * to fix common FUSE kernel module loading problems
    * to create the required but sometimes incorrectly removed or missing FUSE device file

Please note that using setuid-root can result unforeseen privilege escalation and its usage is discouraged. Only the absolutely trusted users must be granted such access. Below is an example how this can be done for users in the ntfsuser group to be able to mount any NTFS volume if they have also the needed volume access rights. chown root.ntfsuser $(which ntfs-3g)
chmod 4750 $(which ntfs-3g) The setuid-root ntfs-3g driver applies the principle of least privilege during its lifetime as a safety measure.
```

---

### Post by nemiux on 2010-06-29
Went there, didn't help.

---

### Post by warfacegod on 2010-06-29
```
The root user can make an ntfs-3g binary setuid-root as shown below
chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g)
```

These didn't work?

---

### Post by Leppie on 2010-06-29
just to make it easy on yourself, remove the fstab entry and install ntfs-config:
```
sudo apt-get install ntfs-config
```

---

