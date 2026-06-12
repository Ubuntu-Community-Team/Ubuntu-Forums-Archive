---
title: "Software Raid 5 Cannot Create FS: Device Busy"
date: 2009-11-21
forum: General Help
---

### Post by cybertron on 2009-11-21
Hey guys... I've been searching and searching and I'm about to pull my bloody hair out. I have followed this tutorial: [http://is.gd/50BiZ](http://is.gd/50BiZ) and I have reached the the part where I create the file system on the raid array but every time I do I get the following output:

> josh@filer:~$ sudo mkfs.ext3 /dev/md0
mke2fs 1.41.9 (22-Aug-2009)
/dev/md0 is apparently in use by the system; will not make a filesystem here!

I have tried killing the mdadm --monitor process, but that didnt fix it. I've tried creating a partition on the drive with fdisk, and I've tried stopping the array with mdadm --stop /dev/md0 but I get the following output:

> josh@filer:~$ sudo mdadm --stop --scan
mdadm: fail to stop array /dev/md0: Device or resource busy



Here is the output of mdadm --detail /dev/md0
> /dev/md0:
        Version : 00.90
  Creation Time : Sat Nov 21 02:08:50 2009
     Raid Level : raid5
     Array Size : 2929653120 (2793.93 GiB 2999.96 GB)
  Used Dev Size : 976551040 (931.31 GiB 999.99 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Nov 21 16:53:22 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1f13d0da:aff1e5de:7cc4f564:e0529720 (local to host filer)
         Events : 0.18

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1



Any idea as to what is going on?

---

### Post by fjgaude on 2009-11-21
Gosh, it looks like you have a fully functional array, with the results of the -D command.

If the array is stopped, then you can unmount it with the normal umount command. Else what goes on here is the OS has mounted it after you re-booted.

Do you have a line in your /etc/fstab file that auto mounts the array?

---

### Post by cybertron on 2009-11-22
> **fjgaude said:**
> Gosh, it looks like you have a fully functional array, with the results of the -D command.

If the array is stopped, then you can unmount it with the normal umount command. Else what goes on here is the OS has mounted it after you re-booted.

Do you have a line in your /etc/fstab file that auto mounts the array?

Well I did skip ahead and add the line from the tutorial to fstab, but the output of "mount" is: 

> /dev/mapper/filer-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /boot type ext2 (rw)

sda is my 250GB OS drive. Also, I cant stop the array as I mentioned above, and nothing seems to be mounted anyways. Maybe I'm missing something with the mdadm monitor... how can I check to see if that is running? here is the output of "ps -A":
> josh@filer:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 kintegrityd/0
   16 ?        00:00:00 kintegrityd/1
   17 ?        00:00:00 kblockd/0
   18 ?        00:00:00 kblockd/1
   19 ?        00:00:00 kacpid
   20 ?        00:00:00 kacpi_notify
   21 ?        00:00:00 kacpi_hotplug
   22 ?        00:00:00 ata/0
   23 ?        00:00:00 ata/1
   24 ?        00:00:00 ata_aux
   25 ?        00:00:00 ksuspend_usbd
   26 ?        00:00:00 khubd
   27 ?        00:00:00 kseriod
   28 ?        00:00:00 kmmcd
   29 ?        00:00:00 bluetooth
   30 ?        00:00:00 khungtaskd
   31 ?        00:00:00 pdflush
   32 ?        00:00:00 pdflush
   33 ?        00:00:00 kswapd0
   34 ?        00:00:00 aio/0
   35 ?        00:00:00 aio/1
   36 ?        00:00:00 ecryptfs-kthrea
   37 ?        00:00:00 crypto/0
   38 ?        00:00:00 crypto/1
   42 ?        00:00:00 scsi_eh_0
   43 ?        00:00:00 scsi_eh_1
   45 ?        00:00:00 kstriped
   46 ?        00:00:00 kmpathd/0
   47 ?        00:00:00 kmpathd/1
   48 ?        00:00:00 kmpath_handlerd
   49 ?        00:00:00 ksnapd
   50 ?        00:00:00 kondemand/0
   51 ?        00:00:00 kondemand/1
   52 ?        00:00:00 kconservative/0
   53 ?        00:00:00 kconservative/1
   54 ?        00:00:00 krfcommd
  133 ?        00:00:00 usbhid_resumer
  279 ?        00:00:00 scsi_eh_2
  306 ?        00:00:00 scsi_eh_3
  307 ?        00:00:00 usb-storage
  324 ?        00:00:00 kdmflush
  341 ?        00:00:00 kdmflush
  409 ?        00:00:00 kjournald2
  443 ?        00:00:01 mountall
  458 ?        00:00:00 upstart-udev-br
  465 ?        00:00:00 udevd
  600 ?        00:00:00 udevd
  601 ?        00:00:00 udevd
  645 ?        00:00:00 edac-poller
  684 ?        00:00:00 kpsmoused
  720 ?        00:00:00 dd
  770 ?        00:00:00 rsyslogd
  912 tty4     00:00:00 getty
  915 tty5     00:00:00 getty
  922 tty2     00:00:00 getty
  923 tty3     00:00:00 getty
  925 tty6     00:00:00 getty
  931 ?        00:00:00 cron
  932 ?        00:00:00 atd
  966 ?        00:00:00 sshd
  968 ?        00:00:00 md0_raid5
  987 ?        00:00:00 kdmflush
 1002 ?        00:00:00 nmbd
 1010 ?        00:00:00 smbd
 1016 ?        00:00:00 smbd
 1029 ?        00:00:00 winbindd
 1031 ?        00:00:00 winbindd
 1076 tty1     00:00:00 getty
 1077 ?        00:00:00 sshd
 1129 ?        00:00:00 sshd
 1130 pts/0    00:00:00 bash
 1267 ?        00:00:00 winbindd
 1268 ?        00:00:00 winbindd
 1337 pts/0    00:00:00 ps


**EDIT**

Also, here is my cat /proc/mdstat:

> josh@filer:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[3] sdd1[2] sdc1[1] sdb1[0]
      2929653120 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>

---

### Post by fjgaude on 2009-11-22
Have you tried commenting out the line in your fstab file that mounts md0 and then re-boot?

Is the UUID in the mdadm.conf file the same as the one shown in the results of the --detail output?

---

### Post by cybertron on 2009-11-22
> **fjgaude said:**
> Have you tried commenting out the line in your fstab file that mounts md0 and then re-boot?

Is the UUID in the mdadm.conf file the same as the one shown in the results of the --detail output?

I actually added that to fstab after my first reboot while having this problem because I thought maybe it would fix the problem... I assumed you needed to mount it before you created an FS, but I see thats not the case. 

I commented that out of fstab and rebooted but nothing changed.

And here is my fstab:

> 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=0.90 spares=1 UUID=1f13d0da:aff1e5de:7cc4f564:e0529720

# This file was auto-generated on Sat, 21 Nov 2009 01:38:02 -0500
# by mkconf $Id$


:~$ sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=1f13d0da:aff1e5de:7cc4f564:e0529720

(On a side note, I did take a zero from "metadata=0.90" it used to be "00.90" and I changed that because of an error I was getting that I found on these forums)

---

### Post by fjgaude on 2009-11-22
Strange... here's what my mount l is:

```
frank@sunshine:~$ mount -l
/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/md32 on /home/raid type ext3 (rw,noatime)
/dev/sdb2 on /media/backup type ext3 (rw) [backup]
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/frank/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=frank)
```

What is that /dev/mapper doing in your mount output?

Everything tells us you have a functional array. Some how something is keeping it from being normal.

---

### Post by cybertron on 2009-11-23
I'm not sure. How would I get it out of there and what is it in the first place? 

Not sure if this is any help, but here is my "fdisk -l"

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b8e72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30370   243946993+  8e  Linux LVM
/dev/sda2           30371       30401      249007+   5  Extended
/dev/sda5           30371       30401      248976   83  Linux

Disk /dev/sdb: 1000.0 GB, 999989182464 bytes
255 heads, 63 sectors/track, 121575 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x912cb4e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121575   976551156   fd  Linux raid autodetect

Disk /dev/sdc: 1000.0 GB, 999989182464 bytes
255 heads, 63 sectors/track, 121575 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84b60c92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121575   976551156   fd  Linux raid autodetect

Disk /dev/sdd: 1000.0 GB, 999989182464 bytes
255 heads, 63 sectors/track, 121575 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058159

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121575   976551156   fd  Linux raid autodetect

Disk /dev/sde: 1000.0 GB, 999989182464 bytes
255 heads, 63 sectors/track, 121575 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121575   976551156   fd  Linux raid autodetect

WARNING: The size of this disk is 3.0 TB (2999964794880 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID
partition table format (GPT).


Disk /dev/md0: 3000.0 GB, 2999964794880 bytes
2 heads, 4 sectors/track, 732413280 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0xadaa7672

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1   536870911  2147483642   83  Linux
josh@filer:~$

```


**EDIT**

Hmm, this is interesting...

```
(parted) print list
Model: ATA WDC WD2500SD-01K (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      32.3kB  250GB  250GB  primary                boot, lvm
 2      250GB   250GB  255MB  extended
 5      250GB   250GB  255MB  logical   ext2


Model: AMCC 9500S-4LP DISK (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Model: AMCC 9500S-4LP DISK (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Model: AMCC 9500S-4LP DISK (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Model: AMCC 9500S-4LP DISK (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary               raid


Error: /dev/mapper/sraid5-wheeljack: unrecognised disk label

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/filer-swap_1: 6182MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  6182MB  6182MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/filer-root: 244GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  244GB  244GB  ext4


Model: Unknown (unknown)
Disk /dev/md0: 3000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


(parted)

```

Notice there is a mention of /dev/mapper blah blah wheeljack. Wheeljack is the name of the share/partition(?) I used when setting up OpenFiler. This setup of disks was used for that, but I never got it working. But after I used openfiler unsuccessfully, I switched back to FreeNAS and had a working raid array and share. Maybe I should redo this whole setup and redo the drives on my raid card. I'll try that first and report back tomorrow.


**edit2**

Something else worth noting, at boot, I see on the console... "Starting MD monitoring service" but that was not in the ps -a I did earlier.

---

### Post by cybertron on 2009-11-23
Ok, now I'm about to strangle myself. I have gone into my 3ware controller.. I'm using a 3ware 9500s card.. and I deleted all the drives (configured as "Single Drive") and set them all up in a RAID0 strip... rebooted, saving changes to the drives, then going back in and setting them all up as "Single Drive" again. 

I've created all the partitions based on the guide I mentioned above, and am now trying to create the array. Here is what I get.

```
josh@filer:~$ sudo mdadm --create --verbose /dev/md2 --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: Cannot open /dev/sde1: Device or resource busy
mdadm: create aborted

```

---

### Post by fjgaude on 2009-11-23
Gosh, you are running into all kinds of things little understood, my me or you.

The 'mapper' usually shows up when someone installs **dmraid**. Such is used when one builds a raid array using the motherboard raid facility.

With a 3ware card you could build a raid5 and it would show up in Ubuntu as one drive.

If you wish to use **mdadm** you must setup the drives as individual drives (JBODs).

You will likely have to zero the superblocks of each drive using mdadm before you can create another array.

```
sudo mdadm --zero-superblock /dev/sd[nn]
```

for each drive.

---

