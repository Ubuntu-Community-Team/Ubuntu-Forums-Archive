---
title: "Switch to Encrypted LVM"
date: 2012-05-06
forum: General Help
---

### Post by Dave_L on 2012-05-06
My current hard disk:

```
Primary partition (50GB, ext4) - Ubuntu 10.04 
Extended partition
... Logical volume (2GB) - swap
... Logical volume (50GB, ext4) - unused
... Unallocated (100GB)
... Logical volume (30GB, ext4) - data
```

I'd like install Ubuntu 12.04 on the unused 50GB logical volume, using full-disk encryption (Encrypted LVM), and leave the existing Ubuntu 10.04 installation unchanged.

Is that possible?  Or would I have to completely rebuild the partitions in order to use Encrypted LVM?

I booted a USB drive created from the ubuntu-12.04-alternate-i386.iso, but when I got to the partitioning step, I couldn't figure out what to do.

I have an external hard drive with 350GB free space, so backing up and restoring the 50GB Ubuntu 10.04 partition and the 30GB data volume would not be a problem.

What do you suggest? :-\"

---

### Post by jerome1232 on 2012-05-06
You'll have to redo the partitions, you have to create one large encrypted partition, put a lvm physical volume in it and go from there.

---

### Post by Dave_L on 2012-05-06
Thanks.

Suppose I back up the 50GB Ubuntu 10.04 partition and the 30GB data volume on my external drive.

After I have the LVM physical volume set up on the internal drive, I'll create 50GB and 30GB logical volumes within the physical volume. Then I'll copy the 50GB Ubuntu 10.04 partition and the 30GB data volume from the external drive to the 50GB and 30GB logical volumes on the internal drive. As part of the LVM physical volume, they'll automatically be encrypted but otherwise will be unchanged.

The grub installed by Ubuntu 12.04 will recognise the Ubuntu 10.04 volume and allow me to boot into it.

Is all that correct? (I'm an LVM newbie :))

---

### Post by Dave_L on 2012-05-08
One issue that occurred to me is that after I restore the 50GB Ubuntu 10.04 partition, I may need to change embedded device references.  For example, an instance of "/dev/sda1" in a configuration file would have to be changed, since the partition will probably have a different path.

/etc/fstab uses UUIDs and labels, rather than absolute paths, so it will probably work as-is. Do you know of any other files that need examining?

---

### Post by jerome1232 on 2012-05-08
If your are already using lvm, and you use the same volume group/logical volumes then the /dev/ paths wont change.

Logical volumes are referred to as /dev/mapper/volume_group-volume_name

---

