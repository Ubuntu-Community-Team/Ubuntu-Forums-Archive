---
title: "Boot Error"
date: 2009-12-31
forum: General Help
---

### Post by kavi_utd on 2009-12-31
Hey guys,

Im a newbie. I had a porblem with my fstab and tried to edit. I did edit and now nothing is working at all. here are the stuff you going to need to rescue me.

**fdisk -l **

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06b72c46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1275       15839   116984816    7  HPFS/NTFS
/dev/sda2           15839       17469    13088868    7  HPFS/NTFS
/dev/sda3           17469       23239    46343714    7  HPFS/NTFS
/dev/sda4           23240       30402    57530078    f  W95 Ext'd (LBA)
/dev/sda5           23240       28703    43889548+  83  Linux
/dev/sda6           28704       30402    13638656    7  HPFS/NTFS

**fstab looks like this**

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda6 during installation
UUID=f155d341-7c88-4098-8763-8d1a0a872f5d  /              ext4         group,user,owner            0  1  

Something is terribly wrong. How can i recover from this terrible situation.

Anyhelp will be highly appreciated.

Thank you,
Kavinga

---

### Post by Leppie on 2009-12-31
First of all welcome to the community.

Second, could you please specify what error you get?

Third, your fstab shows a UUID reference but fdisk -l only shows the /dev references. Could you post the output of:
```
$ls -l /dev/disk/by-uuid
```

Fourth, do you remember what you changed in your fstab?

---

