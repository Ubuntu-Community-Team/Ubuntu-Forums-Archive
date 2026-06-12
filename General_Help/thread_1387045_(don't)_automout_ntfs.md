---
title: "(don't) automout ntfs?"
date: 2010-01-21
forum: General Help
---

### Post by kamina on 2010-01-21
For some reason my Windows partition is being automatically mounted under ubuntu 9.10. I would prefer not to mount it, but as it's not included in fstab I don't know how to stop it...

```

$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d0ae0dc8-9f88-4874-8212-d614474be783 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=dd609331-e9fb-4927-a85d-1e01df32c50f /boot           ext2    defaults        0       2
# videos
/dev/sda7	/media/xbmc					ext4	defaults		0	2

# esata backup
/dev/sdb1	/mnt/backup		ext3	defaults	0	2
# swap was on /dev/sda6 during installation
UUID=fc09b934-73b0-4b3a-aeb0-b9424f139bd1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

The ntfs drive is /dev/sda1

```

$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda2 on /boot type ext2 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /mnt/backup type ext3 (rw)
/dev/sda7 on /media/xbmc type ext4 (rw)

```

---

### Post by kamina on 2010-01-22
Bump

---

### Post by lordskid on 2010-01-22
check /etc/fstab if /dev/sda1 is there if it is there remove it or comment it out by adding # to the beggining of the line.

---

### Post by lordskid on 2010-01-22
try to check too if you have ntfsprog installed or something similar, if you do untick the automount ntfs partition on startup option from there.

---

### Post by Grenage on 2010-01-22
Add the partition to fstab, but use the *noauto* option, that should do it.

---

### Post by kamina on 2010-01-22
> **lordskid said:**
> try to check too if you have ntfsprog installed or something similar, if you do untick the automount ntfs partition on startup option from there.

Nope, not installed. I already got a few options of what might be installed causing it but nothing there. This is a very minimal (server) install with just xbmc installed.

---

### Post by kamina on 2010-01-22
> **Grenage said:**
> Add the partition to fstab, but use the *noauto* option, that should do it.

Thanks, I'll try this when I get home.

---

### Post by Leppie on 2010-01-22
install ntfs-config:
```
sudo apt-get install ntfs-config
```

it will let you configure these things in an easy way.

---

