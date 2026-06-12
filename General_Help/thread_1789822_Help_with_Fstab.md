---
title: "Help with Fstab"
date: 2011-06-24
forum: General Help
---

### Post by strange_cathect on 2011-06-24
Unique issue here. (Ubuntu 10.10)

There is some kind of bug that has bitten me before that causes Ubuntu to confuse drive partitions during (re)install. I have two drives. On one drive I have installed / and /home partitions. Then I have a separate drive that is a backup of /home. For some reason, during a reinstall, ubuntu confused my actual /home with the backup of /home on the other drive. **I am dead certain that I did not make a mistake during install.** I need some help editing fstab so that ubuntu uses my actual /home and not the backup.

/dev/sda3 = /
/dev/sda2 = /home

dev/sdb1 = /home (backup)

Here is my current fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=841868a3-a027-4f40-9d14-c68fb3d5cf80 /home           ext3    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=916aa027-e796-45a9-a358-e4fe5c866c8d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

What do I need to alter here to make ubuntu mount /dev/sda2 as /home??

Thanks.

---

### Post by dandnsmith on 2011-06-24
If you run *blkid*, that will give you a list of the partitions and their UUIDs.
From that you'll have enough info to sort out the fstab entries.

---

### Post by strange_cathect on 2011-06-24
Here are the results:

```
/dev/sda1: UUID="916aa027-e796-45a9-a358-e4fe5c866c8d" TYPE="swap" 
/dev/sda2: UUID="841868a3-a027-4f40-9d14-c68fb3d5cf80" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="9c88acfc-7f2e-4740-b4be-fc449adcd1c3" TYPE="ext4" 
/dev/sdb1: LABEL="Backup" UUID="e8803af6-4c7f-4766-ba6e-be711320494d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="841868a3-a027-4f40-9d14-c68fb3d5cf80" TYPE="ext3" 
/dev/sdc1: LABEL="6178694228" UUID="8C24-A43F" TYPE="vfat" 

```

---

### Post by strange_cathect on 2011-06-24
Ok, this is weird, right?

My /sda2 and /sdb2 have the same UUID:

/dev/sda2: UUID="841868a3-a027-4f40-9d14-c68fb3d5cf80" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="841868a3-a027-4f40-9d14-c68fb3d5cf80" TYPE="ext3" 

That shouldn't happen, right? I suppose this is because I did a backup that preserved the UUID.

Can I change the UUID and make /dev /sda2 my /home partition?

Or could I just delete the backup partition and reboot?

---

### Post by pqwoerituytrueiwoq on 2011-06-24
> **strange_cathect said:**
> Here are the results:

```
/dev/sda1: UUID="916aa027-e796-45a9-a358-e4fe5c866c8d" TYPE="swap" 
/dev/sda2: UUID="**841868a3-a027-4f40-9d14-c68fb3d5cf80**" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="9c88acfc-7f2e-4740-b4be-fc449adcd1c3" TYPE="ext4" 
/dev/sdb1: LABEL="Backup" UUID="e8803af6-4c7f-4766-ba6e-be711320494d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="**841868a3-a027-4f40-9d14-c68fb3d5cf80**" TYPE="ext3" 
/dev/sdc1: LABEL="6178694228" UUID="8C24-A43F" TYPE="vfat" 

```
i think the issue is a redundant uuid i would try selecting the partition with the /dev/sdb2 instead of the uuid
[FONT=Courier New]/dev/sdXX /home           ext3    defaults        0       2[/FONT]
i am not sure which partition you want as /home
look how the XX lines up
[FONT=Courier New]sdXX
sda2
sda3
sdb1
sdb2
sdc1[/FONT]

---

### Post by strange_cathect on 2011-06-24
Hey, thanks for the response.

I want the /sda2 as my /home.

You are right. I have a duplicate UUID because of a backup, I think. So, since they share the same UUID, can I just delete the partition with the backup on it (using livecd). Upon reboot, would fstab just look for the UUID and correctly mount /sda2???

Or can you somehow rename a UUID?

---

### Post by sisco311 on 2011-06-24
> **strange_cathect said:**
> Hey, thanks for the response.

I want the /sda2 as my /home.

You are right. I have a duplicate UUID because of a backup, I think. So, since they share the same UUID, can I just delete the partition with the backup on it. Upon reboot, would fstab just look for the UUID and correctly mount /sda2???

You don't have to delete the backup partition. Simply change its UUID:
```
sudo tune2fs -U random /dev/**sdXY**
```
Where **sdXY** is the device name of the backup partition.

---

### Post by strange_cathect on 2011-06-24
Awesome, sisco. I'll try it now.

---

### Post by strange_cathect on 2011-06-24
Wait, is it ok to do this while it is currently mounted as /home??

---

### Post by strange_cathect on 2011-06-24
Nevermind. I just went for it. Worked like a **charm**. Thanks so much for your help guys!

---

### Post by dino99 on 2011-06-24
> **strange_cathect said:**
> Wait, is it ok to do this while it is currently mounted as /home??

its only the uuid change (info inside a file) so go ahead

but help the system to be not confused:

instead of: dev/sdb1 = /home (backup), change its name a bit (/homeback)

---

