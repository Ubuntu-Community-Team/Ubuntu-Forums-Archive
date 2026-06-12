---
title: "RAID, disk partially crashed, can't boot, help :)"
date: 2012-06-16
forum: General Help
---

### Post by p314i on 2012-06-16
Hi all.

My primary HD is mirrored.  It seems that earlier today one of the two disks decided that it had enough.  Here is the current situation.

sda is plugged into SATA1.
sdb is plugged into SATA2.

Both are split into three partitions(/, swap, /home) and form the mirrored array /md0, /md1, /md2.

output from cat /proc/mdstat is below  

```
rob@Ubuntu:~$ sudo cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdb3[0] sda3[1]
      429786880 blocks [2/2] [UU]
      
md1 : active raid1 sdb2[0] sda2[1]
      9767424 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[0]
      48829440 blocks [2/1] [U_]
      
unused devices: <none>
```

It seems that sda is having issues and should be replaced.  No big deal, I've been through this before.  However, here is the problem.  When I remove sda, it fails to boot (hangs at a black screen with flashing cursor before getting to grub).

According to GParted, both sda1 and sdb1 are labelled as boot, raid.  So I feel like I should be able to boot even after removing sda.  However, it doesn't seem to work.

Obviously, I would like to pull the failed/failing disk out and replace it, however, since I can't boot of sdb, I am stuck.

Any ideas?

---

### Post by p314i on 2012-06-16
An update.

sda is failing more and more.  I tried pulling the drive, booting up to the 12.04 LiveCD and tried to run the [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") application.

Now, with sda removed I get a no operating system error instead of a black screen with a flashing cursor.

I also tried the command line version with the good disk now known as sda
```
sudo grub-install /dev/sda
```
that didn't work because the drive wasn't mounted and I couldn't figure out how to mount it since it is officially part of a RAID.

If it matters, I am running 10.04 amd64.

Anyone have any idea?

---

### Post by p314i on 2012-06-17
One more update.

The good drive is now in the first position (sda).  The failing drive got switched to the second (sdb).

If I try to boot with only the good drive attached I get a 

```
Missing operation system
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```

error message.

When I have both the good and bad drives attached, it boots fine.

At this juncture, I feel like if I could get the boot info off the bad drive and onto the good drive, I should be able to remove the failing drive.  However, my searchfu has been failing me.

Or, is it a situation that I need both drives attached for grub to work?  That seems odd.  I've had to replace a drive in the RAID before and didn't run into any problems once I physically pulled the drive.

---

### Post by p314i on 2012-06-17
Well, getting closer.

After booting with both drives (the good on sda) I ran

```
sudo grub-install /dev/md0
```

That seemed to fix the boot problem since I am up and running with the bad disk removed.  However, I did manage to lose my swap space.  As mentioned earlier, I have my drive broken into 3 pieces, /, swap, and /home.  / and /home were recognised fine, but for some reason it couldn't find my swap space.

The relevant part of /etc/fstab is below:
```

rob@Ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=399c3bcd-5919-4f92-ab60-0340c6ed89f1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/md2
UUID=0c469aa8-1384-4499-8dda-63b15ef17231 /home           ext3    relatime        0       2
# /dev/md1
UUID=6382644c-16aa-4eeb-b04a-964149bfb40d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

It seems the UUID changed?  Not sure.  I would prefer to have some swap space, so off to look for a solution to that problem now.  At least I can boot.

---

### Post by p314i on 2012-06-17
Well, not sure exactly how I fixed it, but roughly speaking, it was showing as inactive, I reactivated it through Disk Utility, reformatted it, got a new UUID from blkid, edited /etc/fstab to reflect that change, and I have swap space back.  Hurray.

---

### Post by YannBuntu on 2012-06-19
Hello
for information, please could you indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?

---

