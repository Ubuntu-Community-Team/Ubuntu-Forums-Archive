---
title: "problem with software RAID 5"
date: 2010-09-15
forum: General Help
---

### Post by msteinbichler on 2010-09-15
First of all: Hello community! ):P

And now to my problem, i hope you can help me.
I'm using Ubuntu 10.04.1 LTS mainly as a storage server. I have one small SSD disk for the system and 3 2TB disks for storage. I want to use those 3 disks in a software RAID 5.

Eventually I allready succeeded in creating this RAID. 
I created it like this:
```

sudo mdadm --create --verbose --chunk 128K /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1 --spare-devices=0

```The RAID set did work perfectly. md0 was usable from the begining on and after a few hours the initial recovery was finished too.
But after a reboot of the system /proc/mdstat shows the following:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md_d0 : inactive sdc1[1](S)
      1953511936 blocks

unused devices: <none>

```And /dev/md0 doesn't exist anymore. If I try to assemble the raid again with:
```

sudo mdadm --assemble -v /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1

```I get the following error:
```

mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted

```Only if i stop the inactive md_d0 with mdadm --stop I can reassemble the RAID5 array. 
But I don't really want to do this after every reboot.

I'd be very thankfull for any advices. Thanks in advance!
Best regards,
Martin

---

### Post by msteinbichler on 2010-09-16
I managed to solve my problem myself. 
I didn't know, I had to add the ARRAY into the mdadm.conf file. I thought the ARRAY would be auto-assembled on boot.

If anyone has the same problem, what I did is:
added all my devices into the mdadm.conf file
```

DEVICE /dev/sdb1
DEVICE /dev/sdc1
DEVICE /dev/sdd1

```

and then I simply used mdadm to add the ARRAY into the config file:
```

mdadm --detail --scan >> mdadm.conf

```

Best Regards,
Martin

---

### Post by iMatter on 2010-09-16
I have exactly the same problem, but this did not work for me, at every re-boot the RAID is not up. This being a RAID1.

root@server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb[1](S)
      488386496 blocks

unused devices: <none>
root@server:~#

The conf file looks like this:

root@server:~# cat /etc/mdadm/mdadm.conf
DEVICE /dev/sda5
DEVICE /dev/sdb5

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5a0c7de3:35f39029:01f9e43d:ac30fbff
root@server:~#

At every boot I have to manually or with a script do:
mdadm --assemble --scan

Then it works, does anyone know what's missing, or what I have missed to do?

I'd be thankful for any answer.

---

### Post by john newbuntu on 2010-09-16
Look through this thread from the beginning.  Somewhere in there lies the solution.
[http://ubuntuforums.org/showthread.php?t=1558568&page=3](http://ubuntuforums.org/showthread.php?t=1558568&page=3)
Sorry to be leading you into a forest rather than a quickfix but hopefully you will solve your problem.

---

### Post by iMatter on 2010-09-16
That thread didn't add anything to my setup or config, that might remedy the fact that the array is not auto-starting. I didn't set a chunksize at creation, is that going to be a problem?

If I type:

root@server:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Sep 16 04:29:41 2010
     Raid Level : raid1
     Array Size : 429778816 (409.87 GiB 440.09 GB)
  Used Dev Size : 429778816 (409.87 GiB 440.09 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Sep 16 15:12:15 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5a0c7de3:35f39029:01f9e43d:ac30fbff (local to host server)
         Events : 0.62

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5

And:
root@server:~# mdadm -Ds
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=5a0c7de3:35f39029:01f9e43d:ac30fbff

The old and new config file is:

root@server:~# cat /etc/mdadm/mdadm.conf
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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5a0c7de3:35f39029:01f9e43d:ac30fbff


I don't see anything that is missing, right now I'm starting the array with a script in rc2.d, and that seems to be the best option, this far.

---

### Post by john newbuntu on 2010-09-16
Did you try running :
sudo dpkg-reconfigure mdadm

---

