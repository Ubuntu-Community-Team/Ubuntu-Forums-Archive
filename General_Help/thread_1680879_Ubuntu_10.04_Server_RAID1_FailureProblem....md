---
title: "Ubuntu 10.04 Server RAID1 Failure/Problem..."
date: 2011-02-03
forum: General Help
---

### Post by ibeeby on 2011-02-03
Folks,

Very sorry if this is an FAQ.

I have a P4 based Ubuntu 10.04 server machine which boots of /dev/sda (60GB IDE) and which has 2* 250GB IDE drives (/dev/sdb and /dev/sdc respectively) which were running as RAID1 as a shared drive.

The machine went down badly yesterday owing to several dirty power outages - for some reason that is for another day the UPS did not protect the machine properly - I returned home to find the system failing to boot.

The system no longer seems to recognise the RAID1 array.  What _was_ /dev/md0 now appears to be /dev/md_d0 (??).  On the Ubuntu Server startup screen I get the message:

'The disk drive for /mnt/raid is not ready yet or not present'

I then have the option of waiting, skipping mounting or manual recovery.

I don't have the knowledge of the mdadm tool to fix this - it may be that there is a problem with one of the disks that the power outage caused or alternatively there may be a problem with the config.  I don't know how to find out.  The server runs xBox/Zentyal normally which appears, sadly, to have no tools to assist me.

Any help gratefully received.

I do want to recover the data on the disk(s).  Needless to say the reason for using the RAID was because there is no alternative backup mechanism for the size of the data files that is stored thereon (ie I am too cheap to buy a tape drive that will cost 2* what this server cost...).

Help please..

Ian

---

### Post by L33ad on 2011-02-03
I'm not 100% sure about rebuilding the broken array.  However, it sounds like your data is still there.  Since it's a mirrored array, you can always just mount one drive as a regular ext4 (or whatever you had it formatted as) and copy the data off to another machine.  Then just wipe and rebuild the array, and copy your data back.

I'd also take the time to run a couple HDD diagnostics.  Seen a lot of hard drives run into problems after power outages.

---

### Post by fabricator4 on 2011-02-03
Turn off the raid and plug each disk in individually so that it mounts as sdb1.  If you're lucky one disk will still have a valid partition table and data.  Raid 1 has each disk in a standard readable format, it's just that they are mirrored.

Once you've recovered the data you can try and work on the disk that is not operational.  Do not write to either disk until you've recovered all the data you can.

If the system does not recognise an sdb device at all then most likely the controller on the drive is fried.  If you can see the sdb device but no partitions then the physical disk itself may be damaged, or something has tromped all over the partition table.

Since the disks are identical you have the option of swapping controllers to get a working drive.  This approach is not for the faint hearted since the connections to the motor and the heads are normally either hard wired or use a conducting block that has to be positioned precisely.

If the data just has to be recovered at all costs, and you can't get one of the mirrored disks to mount as sdb1 then you should consider giving the job to a data recovery service.  They will be able to get the data off the drives, but it will cost.


Chris.

---

### Post by ibeeby on 2011-02-03
Thanks for the speedy replies!!

How do I turn off RAID?  It does not appear to be running.

If I cat /proc/mdstat I get:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]

md_d0 : inactive sdb1[0](S)
      244195904 blocks

unused devices: <none>

Any thoughts?

Ian

---

### Post by psusi on 2011-02-03
Post the output of the following:

sudo fdisk -lu
sudo mdadm -E /dev/sd[bc]1

As for backup, raid is no substitute for backups!  You can get yourself a 500gb external drive these days for like $50 and use that for backups.

---

### Post by ibeeby on 2011-02-03
Right - here goes:

sudo fdisk -lu {note that I did not need the sudo as I was logged in on the console as ubuntu boot had stalled}:


Disk /dev/sda: 61.5 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders, total 120069936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007705a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   115137854    57568896   83  Linux
/dev/sda2       115137855   120069809     2465977+   5  Extended
/dev/sda5       115137918   120069809     2465946   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc0b9d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001   83  Linux

sudo mdadm -E /dev/sdb1 :

/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 8e8a7a5e:cd4ab6c4:e73ef6c3:51f2c869 (local to host gandalf)
  Creation Time : Sat Aug 21 16:15:57 2010
     Raid Level : raid1
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Feb  2 07:39:43 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e6795be4 - correct
         Events : 204


      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1

sudo mdadm -E /dev/sdc1 :

/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 8e8a7a5e:cd4ab6c4:e73ef6c3:51f2c869 (local to host gandalf)
  Creation Time : Sat Aug 21 16:15:57 2010
     Raid Level : raid1
  Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
     Array Size : 244195904 (232.88 GiB 250.06 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Feb  2 07:39:43 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e6795bf6 - correct
         Events : 204


      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1

Hope this assists...

Ian

---

### Post by psusi on 2011-02-03
Looks fine.  When you did the cat /proc/mdstat, was that after choosing to skip, or manual recovery, or from the livecd?

If one of the first two, then try this:

```

sudo mdadm --incremental /dev/sdc1

```

---

### Post by fabricator4 on 2011-02-03
> **ibeeby said:**
> Thanks for the speedy replies!!

How do I turn off RAID?  It does not appear to be running.



If the Raid is done in the system BIOS, enter the BIOS and change it so that it's not operating, or so that the controller acts as a normal IDE controller.  If you have a dedicated RAID controller, pull it out of the machine and plug the first mirrored HDD into the first IDE controller cable.  You'll have to make sure it is jumpered as slave otherwise it won't work.  If you've got a secondary controller (which would be an on-board RAID controller) then it might be enough to just unplug the HDD that you are not testing at the time.  You'll still have to check the jumpers on the drive though.

Chris

---

### Post by psusi on 2011-02-03
> **fabricator4 said:**
> If the Raid is done in the system BIOS, enter the BIOS and change it so that it's not operating, or so that the controller acts as a normal IDE controller.

He is using software raid, not a fakeraid controller.  Also if it were, Linux does not care whether it is in raid mode or not; it treats it exactly the same either way.

---

### Post by ibeeby on 2011-02-04
psusi: Yes, I entered console mode by typing 'M' for manual recovery.

After doing the same thing today I typed mdadm --incremental /dev/sdc1 and got:

mdadm: failed to open /dev/md/d0: File Exists.

Is this some form of RAID lockfile?

fabricator4: Yes, I am using software RAID - this is a simple server arrangement with little money spent.  Regarding earlier remarks, I can of course get a backup drive inexpensively but the reason for RAID was to obtain higher availability - but in this case my power supplier seems to have got the better of my UPS in any event!

Thanks guys for your help and patience.

Ian

---

### Post by psusi on 2011-02-04
Hrm.. Try this:

```

sudo mdadm --stop /dev/md/d0
sudo mdadm --incremental /dev/sd[bc]1

```

---

### Post by ibeeby on 2011-02-05
Ok - output as follows:

mdadm --stop /dev/md/d0
mdadm: stopped /dev/md/d0
mdadm --incremental /dev/sdb1
mdadm: /dev/sdb1 attached to /dev/md/d0, not enough to start safely.
mdadm --incremental /dev/sdc1
mdadm: failed to open /dev/md/d0: File exists.

So it appears that the RAID drive was set up as /dev/md/d0 although all of the pre-crash references were /dev/md0...

Ian

---

