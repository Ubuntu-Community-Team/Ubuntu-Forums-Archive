---
title: "Udevd-work random error on boot on Raid0"
date: 2010-10-12
forum: General Help
---

### Post by JohnFante on 2010-10-12
Sorry in advance for the long post. 

I have a strange problem that I hope somebody can help with.

I have a Raid0 setup (see below for details) connected to the ICH10R raid chip on my Gigabyte EX58-UD4P motherboard.

On every second og third boot I get the following error:

```
udevd-work[157]: inotify_add_watch(6, /dev/dm-1, 10) failed: no such file or directory

udevd-work[179]: inotify_add_watch(6, /dev/dm-1, 10) failed: no such file or directory
```

The system halts for a seconds or two and then boots on like nothing has happend. 

My setup is as follows:

Two 500gb discs in Raid0 on the ICH10R. The first partition 100 mb is a Windows 7 system partition (gaming etc.) and then a 300gb partition for the actual Windos install. Then Ubuntu 10.10 with /, /home, /swap and then five data partitions. Grub is on the Windows system partition.

Ubuntu 10.10 x64 installed via USB. No problems during install. 

Besides that I have 2x300gb dics on the Gigabyte built in raid controller. Installed with a Hackintos setup using Mac software raid.

My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_diefbafiah_Volume05 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_diefbafiah_Volume06 /home           ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume012 /home/Backup    ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume09 /home/Emulatorer ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume010 /home/Games     ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume08 /home/Musik     ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume011 /home/VMware    ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume07 none            swap    sw              0       0
```

The only thing I can see missing is the Windows partitions. They get moutned however and are visible in Natilus (as are the two Mac drives) so they are there. Can that be the problem?

Things get weird thou when I try to use gparted to check if my partitions. Then I get (translated form danish:

```
======================
libparted : 2.3
======================
Can not have a partition outside the dics!
Invalid partitionstabel på /dev/sdb - wrong signatur 4aa7

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
```

Any suggestions?

---

### Post by TheAnachron on 2010-10-12
Tried running some disk checks on those discs? You can install GParted and umount some to check whether they may be damaged.

You can also install the PartitionManager and set a flag for all partitions to mark them fschecked.
Is any error logged in /var/logs/sys belonging to the bootup?

---

### Post by ronparent on 2010-10-13
):PI've been getting very similar errors on booting since at least the 10.10 beta and ignoring them. Maybe if they had bugged me a bit more I would have filed a bug report.

A bit of background. Sometime during the development cycle for 10.10, a new set of symbolic links for raid partitions were established. These are the /dev/dm-* devices and somehow I have not yet fathomed parallel the /dev/mapper devices fakeraid user are so  fond of. In a way they are similar to the software raid designations and more convenient to write than say the /dev/mapper/nvidia_aebhdfib which were and still are the symbolic mappings for the raids. So far so good. However, /dev/dm-0 or /dev/dm-1 seem to alternate as the designations for the raid array as a whole, and, in my case /dev/dm-2 designates the extended raid partiton. None of these have file systems and therefore seem to generate these error on boot. These errors are correct but probably shouldn't be displayed since they seem to have no relevance and just confuse us poor already confounded fakeraid user. I have noted the errors now appear also in my 10.04 and Mint 9 releases that they must represent some part of a master plan for fakeraid implementations. Since Ubuntu fakeraid implementation has had inconsistent handling from release to release I can barely contain my curiosity as to where this is all leading. But I guess I'll just await the next bomb.

---

### Post by Erszebet Lunah on 2010-10-20
I don't have a solution either just saying I got those errors too after upgrading to Kubuntu 10.04 (from 9.10).
I'm also using a fakeraid setup for my boot drives (RAID0).

Everything seems to be working though, except those messages popping up.
Occasionally (like, 1 out of 3) Kubuntu starts checking my disks for errors but so far no real problems have been found.

---

