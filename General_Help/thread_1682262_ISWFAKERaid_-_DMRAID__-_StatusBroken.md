---
title: "ISW/FAKERaid - DMRAID : - Status:Broken"
date: 2011-02-05
forum: General Help
---

### Post by Mr Incredible on 2011-02-05
I am running 64 bit Pinguy which is based on 10.10 x86_64 running 2.6.35-23-generic kernel.

I use a Gigabyte MB in which I have 5 drives installed.  The first 4 are managed by the onboard ICH10R Intel chip in a RAID 0 configuration.  I have windows 7 installed to the raid, and I boot from the Raid array.

I installed 10.10 to the 5th drive which is not controlled by the Intel Software RAID, and installed it on the third partition behind another W7 partition (emergency backup up for booting) and a blank partition.

Other than the install overwriting my Windows bootloader on my main Raid install, the install went fine and is running sweetly.

However, I am at a loss as to how to mount my RAID 0 because the DMRAID utility is giving me information which I do not understand how to resolve to access the RAID array through 10.10

Here's the basic info I get:

```

user@user-linux:~$ sudo dmraid -r
[sudo] password for user: 
/dev/sdd: isw, "isw_dcadegbcfe", GROUP, ok, 976773166 sectors, data@ 0
/dev/sdc: isw, "isw_dcadegbcfe", GROUP, ok, 976773166 sectors, data@ 0
/dev/sdb: isw, "isw_bjcchgcfhh", GROUP, ok, 976773166 sectors, data@ 0
/dev/sda: isw, "isw_dcadegbcfe", GROUP, ok, 976773166 sectors, data@ 0
user@user-linux:~$ sudo dmraid -s
ERROR: isw: wrong number of devices in RAID set "isw_bjcchgcfhh_Volume0" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_dcadegbcfe_Volume0" [3/4] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dcadegbcfe_Volume0" [3/4] on /dev/sdc
ERROR: isw: wrong number of devices in RAID set "isw_dcadegbcfe_Volume0" [3/4] on /dev/sdd
*** Group superset isw_bjcchgcfhh
--> Subset
name   : isw_bjcchgcfhh_Volume0
size   : 976768256
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 1
spares : 0
*** Group superset isw_dcadegbcfe
--> Subset
name   : isw_dcadegbcfe_Volume0
size   : 2930298624
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 3
spares : 0
user@user-linux:~$ sudo dmraid -ay -fisw
ERROR: isw: wrong number of devices in RAID set "isw_bjcchgcfhh_Volume0" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_dcadegbcfe_Volume0" [3/4] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dcadegbcfe_Volume0" [3/4] on /dev/sdc
ERROR: isw: wrong number of devices in RAID set "isw_dcadegbcfe_Volume0" [3/4] on /dev/sdd
RAID set "isw_bjcchgcfhh_Volume0" was not activated
RAID set "isw_dcadegbcfe_Volume0" was not activated
user@user-linux:~$ 
 

```

How do I sort this?

Thanks.

PS be gentle, I am relatively new to Linux and know enough to be dangerous!

---

### Post by dpellegrini on 2011-03-05
I'm seeing similar broken RAID behavior.  I, too, have a Gigabyte mobo w/ ICH10R (GA-EP45-DS3R fwiw).

Instead of striping, I set up RAID5 across 3 drives (@250GB). These are strictly for data.  My OSes are on a separate SSD (dual boot Win7 and Ubuntu 10.10).  I had planned on sharing the RAID to share data in both OSes, but that's a separate concern at the moment, because Ubuntu doesn't see the RAID properly.

Here's the output of dmraid
```
$ sudo dmraid -r
/dev/sdc: isw, "isw_bfjjcdddde", GROUP, ok, 488397166 sectors, data@ 0
/dev/sdb: isw, "isw_cfihieeegi", GROUP, ok, 488397166 sectors, data@ 0
/dev/sda: isw, "isw_cfihieeegi", GROUP, ok, 488397166 sectors, data@ 0
$ sudo dmraid -s
ERROR: isw: wrong number of devices in RAID set "isw_bfjjcdddde_Volume0" [1/3] on /dev/sdc
ERROR: isw: wrong number of devices in RAID set "isw_cfihieeegi_Volume01" [2/3] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_cfihieeegi_Volume01" [2/3] on /dev/sdb
*** Group superset isw_bfjjcdddde
--> Subset
name   : isw_bfjjcdddde_Volume0
size   : 0
stride : 128
type   : raid5_la
status : broken
subsets: 0
devs   : 1
spares : 0
*** Group superset isw_cfihieeegi
--> *Inconsistent* Subset
name   : isw_cfihieeegi_Volume01
size   : 488387840
stride : 128
type   : raid5_la
status : inconsistent
subsets: 0
devs   : 2
spares : 0
```From what I've gathered from other sources, fakeraid volumes should show up under /dev/mapper, but mine is not:
```
$ ls /dev/mapper/
control
```A sysadmin friend and I noodled around trying to get it to work and came up with the following:
```
sudo dmraid -r -E /dev/sda
sudo dmraid -r -E /dev/sdb
sudo dmraid -r -E /dev/sdc
sudo dmraid --format isw -C Volume01 --type 5 --disk "/dev/sda /dev/sdb /dev/sdc"
```This seemed to work briefly.  When I rebooted was able to see the RAID in BIOS, and saw the volume from Windows' disk manager.

However, when I booted next, the RAID was messed up in the BIOS and inaccessible in Win disk manager.  :confused:
So it appears I'm back to square one.

Help!!

---

### Post by dpellegrini on 2011-03-10
After banging my head against this a while longer, I thought I'd change tack and see where it led.  

In BIOS I deleted my RAID5 volume and created a RAID1 volume with 2 of the 3 disks.  After booting into Win7 I created a NTFS partition on the RAID1 volume.  During reboot, for some reason BIOS thought that the new volume was RAID5 with a dead disk.  So I recreated the RAID1 volume and created a NTFS partition, but this time unchecked the "quick format" option.  Reboots henceforth saw the RAID1 volume.

Now when I booted ubuntu, the raid volume showed up in /dev/mapper without me having to do anything.  Disk Utility showed the devices as "RAID Component".  This is progress.

Disk Utility also showed the component devices under"Peripheral Devices".  In addition, they showed up individually under "Places" in the menu bar.  Not good.

Mounting the raid volume resolved that. First, I determined the UUID of the volume by running blkid and looking for the /dev/mapper entry.  In /etc/fstab I added:
    # RAID 1 volume
    UUID=16D4FA0ED4F9F03B    /shared    ntfs    auto,rw,noexec,dev,suid,posix=1    0    3
Ran:
    sudo mount -a
It barked:
    fuse: failed to access mountpoint /shared: No such file or directory
Solved this by:
    sudo mkdir /shared
Then the mount finished without error.

Now Disk Utility shows just the raid volume under "Peripheral Devices".  :-)
It's not all sweetness and light, however.  I can only access /shared as root.  When I tried to chown to my account, it had no effect.  The mount output shows:
    /dev/dm-1 on /shared type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)

One big reason for having the shared partition is to hold my Thunderbird data.  Any suggestions on how to proceed?

Thanks!

David

---

