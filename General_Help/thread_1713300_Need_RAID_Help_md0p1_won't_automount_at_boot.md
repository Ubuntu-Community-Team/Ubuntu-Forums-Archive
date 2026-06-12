---
title: "Need RAID Help: md0p1 won't automount at boot"
date: 2011-03-23
forum: General Help
---

### Post by luceerose on 2011-03-23
If you want, skip straight to the 'QUESTION' at the end of my post & refer to the 'EXPLANATION' later.

EXPLANATION:
Using Debian 6.01 Squeeze 64-bit.
Just put together a brand new 3.3Ghz 6-core AMD. I had a nightmare with my Highpoint 640 raid controller, apparently because Debian Squeeze now handles raid through sysfs rather than /proc/scsi. The solution to this, of course, is to recompile the kernel with the appropriate module for /proc/scsi support. So I thought "screw that" and I've yanked out the raid card & went with Debians software raid.
This allowed me to basically complete my mission. The raid is totally up and running, except for one final step... I can't get the raid to automount at boot.

My hardware setup;
- Debian is running totally on a 64Gb SSD.
(sda)
- I have 3x 2Tb hard drives used for storage on a raid 1 array
(sdc,sdd,sde)

This is how I set up;
- All drives were formatted ext4 with a GPT allocation table
Step 1) Installed Debian with manual partition layout, designating sdc1,sdd1,sde1 for use as 'Physical Volume for Raid'
Step 2) After initial install, performed update & reboot.
Step 3) Installed mdadm via Synaptic which then started building the array from sdc1,sdd1,sde1
Step 4) Went to sleep for the night while the array built.
Step 5) Formatted md0 with gparted (GPT,ext4,Volume Label=Home)
Step 6) Rebooted just in case

After all that, the raid seems to work perfectly.
I created a mount point for it with;
```

sudo mkdir -p /media/HomeRaid

```
I can mount it with;
```

mount -t ext4 /dev/md0p1 /media/HomeRaid

```
After unmounting I have to start the Array again by opening nautilus, going to 'Computer', right-click on the raid & click 'Start Multi-disk Drive' before I can mount again.

I can also mount just by selecting it from the Places menu rather than using the command line.

QUESTION:
Ok. So after all that explanation, ultimately I have 2 problems.
Firstly, I seem to need root permissions to mount md0p1. (mounting via Places menu asks for password)
Secondly, I can't for the life of me figure out how to get it to mount automatically at boot.

My fstab file;
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=410d3d0c-4642-4fc3-87ee-108b74ca4581 /               ext4    errors=remount-ro 0       0
# swap was on /dev/sda3 during installation
UUID=9e00024e-c722-4c76-805f-4b0e3f7bfda0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/md0p1	/media/HomeRaid	ext4	rw,user,auto,exec	0	0

```
My /etc/mdadm/mdadm.conf file;
```

DEVICE partitions
MAILADDR root

```
Obviously I've tried adding /dev/md0p1 to the fstab file to the best of my ability. It just doesn't want to work

---

### Post by luceerose on 2011-03-24
COMPLETE SUCCESS

I suspected all along that the drives permissions might be part of the problem.
Anyway, for anyone with the same issue, this is how I solved it;
I updated mdadm.conf with;
```
mdadm -Esc partition | grep ARRAY >> /etc/mdadm/mdadm.conf
```
I actually had to su to do that, it would not allow that command from sudo.

Then, I just did gksu nautilus to right-click on the drive & change permissions to my username instead of root.

Problem solved.
When I rebooted the drive was mounted on the desktop.

---

