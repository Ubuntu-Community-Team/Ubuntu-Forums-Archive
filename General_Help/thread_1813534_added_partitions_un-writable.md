---
title: "added partitions un-writable"
date: 2011-07-27
forum: General Help
---

### Post by manuleka on 2011-07-27
i added two fat32 partitions on fstab
```

/dev/sda5 /home/manu/Others/Dat1 vfat defaults 0 0
/dev/sda6 /home/manu/Others/Dat2 vfat defaults 0 0

```
now both partitions are readily mounted on boot but i can't write/alter any of it's contents

it's a single user installation

mount command output
```

/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda5 on /home/manu/Others/Dat1 type vfat (rw)
/dev/sda6 on /home/manu/Others/Dat2 type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/manu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=manu)

```

help please...

---

### Post by Kira_Belka on 2011-07-27
/dev/sda5 /home/manu/Others/Dat1 vfat defaults rw 0 0
/dev/sda6 /home/manu/Others/Dat2 vfat defaults rw 0 0

---

### Post by manuleka on 2011-07-28
> **Kira_Belka said:**
> /dev/sda5 /home/manu/Others/Dat1 vfat defaults rw 0 0
/dev/sda6 /home/manu/Others/Dat2 vfat defaults rw 0 0

that didn't do anything :(

---

### Post by Elfy on 2011-07-28
Just going out of the door - but check here for vfat

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Wayne_V on 2011-07-28
are you sure it's just not writable only by root?   The mount output shows  it as rw.

see the FAT section under 'man mount'.  You probably need to add uid/gid and maybe umask/dmask options to fstab to mount it owned by the user you would like.

---

### Post by manuleka on 2011-07-28
all i did was add the lines
```
/dev/sda5 /home/manu/Others/Dat1 vfat defaults 0 0
/dev/sda6 /home/manu/Others/Dat2 vfat defaults 0 0
```

to fstab which automounts the partitions

i don't know how to make it writable by user and stuff like that, BUT it is writable by root, i want to be able to use the drives as user also

cheers

---

### Post by Wayne_V on 2011-07-28
from 'man mount':

Mount options for fat
       (Note: fat is not a separate filesystem, but a common part of the msdos, umsdos and vfat filesystems.)

       blocksize={512|1024|2048}
              Set blocksize (default 512). This option is obsolete.

       uid=value and gid=value
              Set the owner and group of all files.  (Default: the uid and gid of the current process.)

       umask=value
              Set the umask (the bitmask of the permissions that are not present). The default is the umask of the current
              process.  The value is given in octal.


so, run 'id manu' to find your uid/gid and then add them to the options in /etc/fstab

---

### Post by manuleka on 2011-07-28
```

uid=1000(manu) gid=1000(manu) groups=1000(manu),4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare)

```

so i just add uid=1000 and gid=1000? sorry i'm a newbie so all these are like first-time to me

---

### Post by Wayne_V on 2011-07-28
yes, just follow the examples in the existing fstab entries:

/dev/sda5 /home/manu/Others/Dat1 vfat rw,uid=1000,gid=1000  0 0

---

### Post by manuleka on 2011-07-28
> **Wayne_V said:**
> yes, just follow the examples in the existing fstab entries:

/dev/sda5 /home/manu/Others/Dat1 vfat rw,uid=1000,gid=1000  0 0

i added this to fstab and it seems to work, correct me if this isn't the right way

```
/dev/sda5 /home/manu/Others/Dat1 vfat auto,users,uid=1000,gid=1000 0 0
/dev/sda6 /home/manu/Others/Dat1 vfat auto,users,uid=1000,gid=1000 0 0
```

---

### Post by Wayne_V on 2011-07-28
that should be fine

---

