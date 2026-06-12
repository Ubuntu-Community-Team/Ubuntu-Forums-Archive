---
title: "RAID array won't assemble"
date: 2011-06-11
forum: General Help
---

### Post by rrrrrichard on 2011-06-11
I rebooted my server and out of nowhere the RAID5 array won't assemble.  I've tried everything I could think of to reassemble the thing.  I fear that the array is ruined, but I can't imagine how.  It had been running just fine for a couple of weeks.

Here are various bits of information:

The simplest failure (with and without partition numbers, which have not been needed in the past):

```
richard@nas:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sd[bcd]
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has no superblock - assembly aborted
richard@nas:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sd[bcd]1
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted

```

Examine output, which I thought was based on the allegedly missing superblocks(?):

```
richard@nas:~$ sudo mdadm --examine /dev/sd[bcd]
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 77e4d604:b6c978a4:6813200f:84871378
           Name : nas:0  (local to host nas)
  Creation Time : Thu May 26 13:24:15 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 3a2e783b:b9f8dc20:0ecd6e62:b9fae232

    Update Time : Fri Jun 10 16:13:54 2011
       Checksum : 72a1e03b - correct
         Events : 37413

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 77e4d604:b6c978a4:6813200f:84871378
           Name : nas:0  (local to host nas)
  Creation Time : Thu May 26 13:24:15 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : d17a11b5:ff9416d4:3e936126:0e1bb143

    Update Time : Fri Jun 10 16:13:54 2011
       Checksum : 7435af9f - correct
         Events : 37413

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 77e4d604:b6c978a4:6813200f:84871378
           Name : nas:0  (local to host nas)
  Creation Time : Thu May 26 13:24:15 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7dc78551:cdb7b6bc:b80e930f:38dc29ec

    Update Time : Fri Jun 10 16:13:54 2011
       Checksum : 8af45bbf - correct
         Events : 37413

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)

```

Fdisk:

```
richard@nas:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000660a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      180362  1448753152   83  Linux
/dev/sda2          180362      182402    16384000   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016c4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00008836

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000fe21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

```

Discouraging /proc/mdstat:

```
richard@nas:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd[3](S) sdc[1](S) sdb[0](S)
      5860540680 blocks super 1.2
       
unused devices: <none>

```
The conf file that used to work:

```
richard@nas:~$ more /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

AUTO -ALL

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sd[bcd]

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR richard@reich.com

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=77e4d604:b6c978a4:6813200f:84871378 name=nas:0 bitmap=/var/mdadm/bitmaps/md0.bitmap

```

I'll be extremely grateful for any suggestions.  Well, maybe not for "recreate the thing".

---

### Post by amauk on 2011-06-11
try using --force
```
sudo mdadm --assemble [COLOR="Red"]--force[/COLOR] --verbose /dev/md0 /dev/sd[bcd]
```

---

### Post by rrrrrichard on 2011-06-11
Thanks, but same result.

```
richard@nas:~$ sudo mdadm --assemble --force --verbose /dev/md0 /dev/sd[bcd]
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has no superblock - assembly aborted

```

---

### Post by YesWeCan on 2011-06-11
Your mdadm.conf may need adjusting. It seems to be best not to define specific devices but just the UUID. The ARRAY statement specifies /dev/md/0 rather than /dev/md0.

I would try changing 'DEVICE /dev/sd[bcd]' to '[COLOR="DarkGreen"]DEVICE partitions[/COLOR]'
and the ARRAY statement to
[COLOR="DarkGreen"]ARRAY /dev/md0 metadata=1.2 UUID=77e4d604:b6c978a4:6813200f:84871378 name=nas:0 bitmap=/var/mdadm/bitmaps/md0.bitmap[/COLOR]

Then try
sudo mdadm --stop /dev/md/0
sudo mdadm --assemble --scan
See if /dev/md0 is now running

Check fstab mounts /dev/md0
If all that works
sudo update-initramfs -u

---

### Post by rrrrrichard on 2011-06-11
Thanks for the idea.  No luck.

```
richard@nas:~$ sudo vi /etc/mdadm/mdadm.conf 
richard@nas:~$ sudo mdadm --stop /dev/md/0
mdadm: error opening /dev/md/0: No such file or directory
richard@nas:~$ sudo mdadm --assemble --scan
richard@nas:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc[1](S) sdd[3](S) sdb[0](S)
      5860540680 blocks super 1.2
       
unused devices: <none>
richard@nas:~$ sudo mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
richard@nas:~$ sudo mdadm -D /dev/md0 
mdadm: md device /dev/md0 does not appear to be active.
richard@nas:~$ sudo mdadm --assemble --scan --verbose
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has wrong uuid.
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: /dev/sdd1 has wrong uuid.

```

With current conf (note I commented out the AUTO, since I don't really know why it's there):

```
richard@nas:~$ more /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

#AUTO -ALL

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR richard@reich.com

# definitions of existing MD arrays
ARRAY /dev/md0 metadata=1.2 UUID=77e4d604:b6c978a4:6813200f:84871378 name=nas:0 bitmap=/var/mdadm/bitmaps/md0.bitmap

```

This was not a big surprise, since the old conf worked though I like the improvements you suggested.

Back to the particular errors mdadm displayed, I've been puzzled from the start of these troubles by the meaning of, for example:

```
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.

```

Is mdadm really having trouble opening the device, or is this just an unhappy choice of error messages by the developer?  It does, immediately after reporting a failure to open the device, complain about the same device's contents!  Which error is real?  Seems hard to believe it can be both.  If the primary problem is failure to open the device, perhaps the second error (UUID wrong) is just a slightly inappropriate report of what it was looking for when it failed to open?  Does anyone know for certain?

Every error I've seen reported has begun with a "cannot open" and then included some confusing (to me) report of something wrong with the content (that presumably cannot be seen).

If the primary issue is the failure to open, is it really because the device is busy?  With what?  Any ideas?  I'm fresh out.

Thanks again for anything.

---

### Post by rrrrrichard on 2011-06-11
Got it!

Apparently something was being locked up by another part of the md empire.

I looked at /etc/default/mdadm and changed it to the following.  Sorry I don't have the original, but I was pretty sure I was going down a blind alley and didn't keep it.  I can tell you with certainty that I flipped all the booleans.  I suspect (will experiment later) the important thing is START_DAEMON.

```
richard@nas:~$ more /etc/default/mdadm 
# mdadm Debian configuration
#
# You can run 'dpkg-reconfigure mdadm' to modify the values in this file, if
# you want. You can also change the values here and changes will be preserved.
# Do note that only the values are preserved; the rest of the file is
# rewritten.
#

# AUTOCHECK:
#   should mdadm run periodic redundancy checks over your arrays? See
#   /etc/cron.d/mdadm.
AUTOCHECK=false

# START_DAEMON:
#   should mdadm start the MD monitoring daemon during boot?
START_DAEMON=false

# DAEMON_OPTIONS:
#   additional options to pass to the daemon.
DAEMON_OPTIONS="--syslog"

# VERBOSE:
#   if this variable is set to true, mdadm will be a little more verbose e.g.
#   when creating the initramfs.
VERBOSE=true

# MAIL_TO:
#   this variable is now managed in /etc/mdadm/mdadm.conf (MAILADDR).
#   Please see mdadm.conf(5).

```

I doubt this is a good permanent solution.  I know that I've been running an md daemon (this one?) in the past.  I'll continue to tweak stuff.  But I've got my data!

So how did all this (whatever it was) happen?  I did an apt-get upgrade yesterday.  I checked the log and it did mess with mdadm.

Here's the good news for posterity:

```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-server x86_64)
Last login: Sat Jun 11 10:49:14 2011 from bizou.reich.com
richard@nas:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
richard@nas:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sd[bcd]
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdc to /dev/md0 as 1
mdadm: added /dev/sdd to /dev/md0 as 2
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: /dev/md0 has been started with 3 drives.
richard@nas:~$ sudo mount -a
richard@nas:~$ ls /raidarray/

```

Thanks to those who helped!

---

