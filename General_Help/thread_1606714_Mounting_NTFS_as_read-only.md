---
title: "Mounting NTFS as read-only"
date: 2010-10-26
forum: General Help
---

### Post by mdrg on 2010-10-26
My PC have 3 NTFS partitions (main and backups) plus Ubuntu 10.10 on dual boot. I want to keep NTFS partitions available, but mounted as read-only by default, so that other users (and accidentally even me) do not modify them in a harmful way.

If possible, I'd like that only root could change the default permissions, so that none of the other users could modify them without switching to Windows. If not possible, making NTFS unmountable would be OK too.

Searching around, I found about pysdm (Storage Device Manager), so I installed it, set all my NTFS partitions as mountable by any user, and as read only, and restarted. Then I couldn't mount the partitions:

```
Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at http://ntfs-3g.org/support.html#unprivileged
```

After some reading it seems that mounting the partitions as root is not a good idea. So, how can I allow the mounting (by any user) without root?

Also, I read that ntfs-3g seems to be the safest lib for NTFS read/write. Does 10.10 uses ntfs-3g by default? If not, should I change it?

Also, I'm a beginner user on Linux environment, so I prefer GUI-based solutions, but if it can't be done or it is simply safer by command line, I'm fine.

Other info:

My fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=4a5ff937-5220-4b4e-b994-304ba37d3448 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=a0285d57-8247-4efe-88ca-14bee4b8630b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Mount -v with all NTFS partitions mounted:
```
/dev/sda1 on /media/1A7099D97099BC47 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 on /media/Stuff type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

Thanks!

---

### Post by dcstar on 2010-10-27
> **mdrg said:**
> My PC have 3 NTFS partitions (main and backups) plus Ubuntu 10.10 on dual boot. I want to keep NTFS partitions available, but mounted as read-only by default, so that other users (and accidentally even me) do not modify them in a harmful way.

If possible, I'd like that only root could change the default permissions, so that none of the other users could modify them without switching to Windows. If not possible, making NTFS unmountable would be OK too.

Searching around, I found about pysdm (Storage Device Manager), so I installed it, set all my NTFS partitions as mountable by any user, and as read only, and restarted. Then I couldn't mount the partitions:
..........

Partitions should be mounted at boot-up, there is no need whatsoever for a "user" to have to manually mount a partition - do not use that option.

You should also mount partitions **outside** of any Linux system folders (like /media) that are for the exclusive use of the Linux system, not you. Create mount points (folders) elsewhere with the appropriate permissions to manage user access with the following (as an example):

```
sudo mkdir /Windows1
chmod **nnn** /Windows1
```
replacing the "**nnn**" with whatever is appropriate and then mounting the partition on that mount point.

---

### Post by mdrg on 2010-10-27
> **dcstar said:**
> Partitions should be mounted at boot-up, there is no need whatsoever for a "user" to have to manually mount a partition - do not use that option.

Ok, fair enough. :)

> **dcstar said:**
> You should also mount partitions **outside** of any Linux system folders (like /media) that are for the exclusive use of the Linux system, not you. Create mount points (folders) elsewhere with the appropriate permissions to manage user access with the following (as an example):

```
sudo mkdir /Windows1
chmod **nnn** /Windows1
```
replacing the "**nnn**" with whatever is appropriate and then mounting the partition on that mount point.

Then say I create /ntfs/win1 folder for my first partition and set the permissions. I'd set the fstab like this:

```
/dev/sda1        /ntfs/win1  ntfs-3g    defaults,ro 0       0
```

Is that right? I just don't know what to do about encoding, umask, fmask or dmask... (will try it tonight)
And if I explicitly wants to write something to this partition? would I need to unmount and mount it again? Or is there any other more user-friendly way?

Thanks again!

---

### Post by linux-hack on 2010-10-27
> **mdrg said:**
> 

```
/dev/sda1        /ntfs/win1  ntfs-3g    defaults,ro 0       0
```

Is that right? I just don't know what to do about encoding, umask, fmask or dmask... (will try it tonight)
And if I explicitly wants to write something to this partition? would I need to unmount and mount it again? Or is there any other more user-friendly way?

Thanks again!

The fstab entry is corect

If you mount it on read only you need to umount and remount to write on it. why not moun it on write and just change the permission on the HD so you'll be the only personne to be able to write on it

---

### Post by Morbius1 on 2010-10-27
> Then say I create /ntfs/win1 folder for my first partition and set the permissions. I'd set the fstab like this:

     Code:
     /dev/sda1        /ntfs/win1  ntfs-3g    defaults,ro 0       0 
Is that right? I just don't know what to do about encoding, umask, fmask or dmask... (will try it tonight)
And if I explicitly wants to write something to this partition? would I  need to unmount and mount it again? Or is there any other more  user-friendly way?
umask, fmask, and dmask are all related to read / write permissions. Your original requirement was to mount them as read only. If you now want the option at some futue date to write to that partition then you might consider the following:

```
 /dev/sda1        /ntfs/win1  ntfs-3g    defaults,umask=022 0       0
```This will mount /dev/sda1 to /ntfs/win1 with owner = root and permissions for root to write to that partition ( the first "0" in umask ). All other users ( and that would be you ) will have read only access ( the "2"'s in umask because of their position will turn off write access to anyone who isn't root ).

This way you will need to be root ( i.e., gksu nautilus or gksu gedit ) to write to those partitions making accidental writes more difficult.

---

### Post by mdrg on 2010-10-27
> **Morbius1 said:**
> ```
 /dev/sda1        /ntfs/win1  ntfs-3g    defaults,umask=022 0       0
```

Worked like a charm! Many thanks! :D

And thanks for the 'gksu' tip. Very useful indeed!

---

