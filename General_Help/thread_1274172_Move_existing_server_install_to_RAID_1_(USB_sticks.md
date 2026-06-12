---
title: "Move existing server install to RAID 1 (USB sticks)"
date: 2009-09-24
forum: General Help
---

### Post by atconc on 2009-09-24
Hi all

I recently updated my home file server box to use a fresh install of Ubuntu server 9.04 - I have 2 RAID 5 sets in the box (3x500GB and 3x1TB) and no more drive bays, so I decided to install the OS to a 8gb USB flash drive (also thinking this would save on noise and power as the SATA drives can spin down when idle).

However, I'm now starting to get nervous about the how long the flash drive is going to survive, and I like the idea of adding a second USB drive as a RAID 1 mirror (hopefully also giving a bit of a read performance boost as the drive is a bit slow).

I've been searching for a guide on how to migrate a single drive install to RAID but haven't found exactly what I need - can anyone help with how I would migrate this>?

(more details)

I accepted the default file system options during the install (I think it used LVM) and have moved some frequently written stuff to tempfs to try to save wear on the stick - he's the output of mount:

```

/dev/mapper/triad-root on / type ext3 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-server/volatile type tmpfs (rw,mode=755)
/dev/sdg5 on /boot type ext2 (rw,noatime)
tmpfs on /tmp type tmpfs (rw)
tmpfs on /var/tmp type tmpfs (rw)
tmpfs on /var/lock type tmpfs (rw)
/dev/md0 on /media/raid type ext3 (rw,noatime,nodiratime)
/dev/md1 on /media/tera type ext3 (rw,noatime,nodiratime)
securityfs on /sys/kernel/security type securityfs (rw)

```

Thanks in advance for any suggestions

---

