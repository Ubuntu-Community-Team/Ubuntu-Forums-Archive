---
title: "expand raid array. now have &quot;no space left on device&quot;"
date: 2011-08-14
forum: General Help
---

### Post by richardedwards on 2011-08-14
Afternoon all,

I have been using Natty (11.04) for a while with a 3disk RAID5 via MDADM and all have been ok.

I have just stuck in another disk using: 

mdadm /dev/md0 --add /dev/sdb, then mdadm --grow /dev/md --raid-devices=4

I then resize2fs /dev/md0

all seemed ok until i tried "tail -f /var/log/syslog" and was given:

tail: cannot watch `/var/log/syslog': No space left on device

df -h gives me loads of space free
df -i no problems

any help would be appreciated as i have an expensive lump parts just sitting here doing nothing.

thanks

richard

---

### Post by Habitual on 2011-08-14
> **richardedwards said:**
> I have just stuck in another disk using: 

mdadm /dev/md0 --add /dev/sdb, then mdadm --grow /dev/md --raid-devices=4

Richard, is that a typo? b/c it should be --grow /dev/md0

---

### Post by richardedwards on 2011-08-14
good spot...yeah it was a typo.

any ideas?

thx

---

### Post by richardedwards on 2011-08-15
*bump*

anyone able to point me in the right direction?

---

### Post by Habitual on 2011-08-15
richard:

I suspect that some room is required on the mount to actually grow it.

Are there any files approaching 2G that you can move/zip or delete?

This should identify some of those, if they exist
```
sudo find `pwd` / -size +1500M

```

you can safely ignore 
```
find: `/home/$user/.gvfs': Permission denied
```

---

### Post by richardedwards on 2011-08-15
The mount has grown and there is loads of room:

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              1.4T 1022G  285G  79% /
none                  2.0G  752K  2.0G   1% /dev
none                  2.0G  488K  2.0G   1% /dev/shm
none                  2.0G  2.4M  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/home/richard/.Private
                      1.4T 1022G  285G  79% /home/richard

---

### Post by richardedwards on 2011-08-15
but i try to run this and get the no space message:

tail: cannot watch `/var/log/syslog': No space left on device

---

### Post by YesWeCan on 2011-08-15
How about a file system check?
Boot live CD,
sudo apt-get install mdadm
sudo mdadm -As
sudo fsck -CV /dev/md0


And how much space are your log files consuming?

---

### Post by richardedwards on 2011-08-16
Evening all,

I ran "fsck -CV /dev/md0"

restarted and same error when trying tail on syslog

/var/log is 80meg

losing the will at the moment...

---

### Post by richardedwards on 2011-08-17
anyone know if i can pay for some support somewhere as I am stuck on this issue and not going anywhere fast....

---

### Post by coffee412 on 2011-08-17
> mdadm /dev/md0 --add /dev/sdb, then mdadm --grow /dev/md --raid-devices=4Try /dev/sdb1(2,3,4,) instead of just /dev/sdb.

That most likely is your problem. Alot of people make that mistake your not alone.

Pay me :D:D:D:D:D

BTW ----

To just add a drive to the array your going to use :

> mdadm /dev/md0 -a /dev/sdb1

Short and sweet.

---

### Post by YesWeCan on 2011-08-17
Ignore. I'll wait to see if coffee412s suggestion works.

---

### Post by richardedwards on 2011-08-17
adding the disk, growing the array and extending the file system isnt the problem...

it is now that i have done all that, without errors or anything untoward, is that i now get the "no space left on device" errors.

a search across the forums, and was suggested on here, was to run the fsck to see what pops up. again nothing that shouldnt be there.

so to summarize: i have gone from a 3disk raid5 setup which was all working perfectly. added another disk to the array, grew the array and extended the partition. nothing else changed. 

thanks for your help...

rich

---

### Post by coffee412 on 2011-08-17
Iam more than happy to help you with your problem but we will need to check some things first before we begin. First, Lets check the current state of the array - Please post the output of 

> mdadm --detail /dev/md0

We need this info to see the current state of your raid. Then we will proceed from there to get things back in working order. This shouldnt take long.

coffee

---

### Post by richardedwards on 2011-08-18
Thanks Coffee412, will not be able to get the information over to you until Friday.

I did a little fiddling with the RAID last night and I left it looking a little sick when I went to bed. Hope I don't need to resort to my untested "DR" solution...

thanks again for the help

richard

---

### Post by richardedwards on 2011-08-20
Morning all,

Output of "mdadm --detail /dev/md0".

thank you.

richard


/dev/md0:
        Version : 0.90
  Creation Time : Sat Mar 12 22:47:02 2011
     Raid Level : raid5
     Array Size : 1465153344 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488384448 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Aug 20 11:47:04 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : ab5a6130:28390767:e9e97aa2:04ec3c9f
         Events : 0.9651

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1
       3       8       16        3      active sync   /dev/sdb

---

### Post by YesWeCan on 2011-08-20
Would you describe what is actually not working in more detail. It is not clear to me.

> all seemed ok until i tried "tail -f /var/log/syslog" and was given:

tail: cannot watch `/var/log/syslog': No space left on device
So what...you can boot Natty off the array but when you run that specific command you get an error. So what then? Is everything else working?

> any help would be appreciated as i have an expensive lump parts just sitting here doing nothing.
What do you mean it is "just sitting here doing nothing"? That sounds like it won't boot.

So what exactly will and won't it do?

---

### Post by YesWeCan on 2011-08-20
> **richardedwards said:**
> Output of "mdadm --detail /dev/md0".
    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1
       3       8       16        3      active sync   /dev/sdb
So why have you got 3 devices that are partitions and one that is a whole disk? Was that intentional?
I believe that when you add a disk or partition to a RAID5 that its size has to be at least as big as the others. Did you check this? Let's see:
sudo sfdisk -luS

Of course, if things were not right you would expect mdadm to report an error when adding the new device. That's not to rule out the possibility that mdadm is malfunctioning. I am not aware of any reason /dev/sdb should not work and /dev/sdb1 should.


To see the whole picture more outputs may help:
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
sudo blkid
cat /etc/fstatb

---

### Post by richardedwards on 2011-08-27
apologies for the delay in replying...

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1          2048 976771071  976769024  fd  Linux RAID autodetect
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an MSDOS signature
 /dev/sdb: unrecognised partition table type
No partitions found

Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *      2048 976771071  976769024  fd  Linux RAID autodetect
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

Disk /dev/sdd: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1          2048 976771071  976769024  fd  Linux RAID autodetect
/dev/sdd2             0         -          0   0  Empty
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty

Disk /dev/md0: 366288336 cylinders, 2 heads, 4 sectors/track

sfdisk: ERROR: sector 0 does not have an MSDOS signature
 /dev/md0: unrecognised partition table type
No partitions found


richard@homesv1:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [ra
id10]
md0 : active raid5 sdc1[2] sda1[1] sdd1[0] sdb[3]
      1465153344 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>


richard@homesv1:~$ cat /etc/mdadm/mdadm.conf
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
MAILADDR [email]myemailaddress@gmail.com[/email]

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=ab5a6130:28390767:e9e97aa2:04ec3c9
f

# This file was auto-generated on Sat, 12 Mar 2011 22:57:40 +0000
# by mkconf $Id$


richard@homesv1:~$ sudo blkid
/dev/sda1: UUID="ab5a6130-2839-0767-e9e9-7aa204ec3c9f" TYPE="linux_raid_member"
/dev/sdb: UUID="ab5a6130-2839-0767-e9e9-7aa204ec3c9f" TYPE="linux_raid_member"
/dev/sdc1: UUID="ab5a6130-2839-0767-e9e9-7aa204ec3c9f" TYPE="linux_raid_member"
/dev/sdd1: UUID="ab5a6130-2839-0767-e9e9-7aa204ec3c9f" TYPE="linux_raid_member"
/dev/md0: UUID="41c8ad59-849a-4aec-8ebb-57ebe22a8805" TYPE="ext4"

Typo on "cat /etc/fstatb"?

richard@homesv1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=41c8ad59-849a-4aec-8ebb-57ebe22a8805 /               ext4    errors=remount
-ro 0       1

thanks again for the help

---

### Post by richardedwards on 2011-08-28
*bump*

thanks all

---

### Post by coffee412 on 2011-08-28
Which dev below does not belong?

> 0       8       49        0      active sync   /dev/sdd1
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1
       3       8       16        3      active sync   /dev/sdb

First, Remove /dev/sdb from the array. Then, Using fdisk make a partition on /dev/sdb. This partition should be the whole drive. Then add /dev/sdb1 into the array.

Done.

---

### Post by richardedwards on 2011-08-29
Done.

Same error....

Whilst it doesn't seem to be affecting the system, email and mythtv have stopped working - but I can't be sure it is connected to this issue as I don't use them enough to say they stopped working at the same time.

Thanks

---

### Post by richardedwards on 2011-08-29
sfdisk - luS

^Crichard@homesv1:~$ sudo sfdisk -luS

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1          2048 976771071  976769024  fd  Linux RAID autodetect
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1          2048 976773119  976771072  83  Linux
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/sdc: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1   *      2048 976771071  976769024  fd  Linux RAID autodetect
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

Disk /dev/sdd: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1          2048 976771071  976769024  fd  Linux RAID autodetect
/dev/sdd2             0         -          0   0  Empty
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty

Disk /dev/md0: 366288336 cylinders, 2 heads, 4 sectors/track

sfdisk: ERROR: sector 0 does not have an MSDOS signature
 /dev/md0: unrecognised partition table type
No partitions found

---

### Post by coffee412 on 2011-08-29
Can you please repost the output of the following:

> mdadm --detail /dev/md0
and

> fdisk -lI have the same dos error on my array (raid5 / 4 disks) but you can ignore that dos error. 

coffee

---

