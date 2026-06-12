---
title: "RAID works, but not after reboot"
date: 2011-05-29
forum: General Help
---

### Post by Kissell on 2011-05-29
When the computer boots the software raid array at /dev/md0 doesn't start on its own. 

I do "pg /proc/mdstat" and see:
> 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md126 : inactive sdp1[14](S) sdm1[13](S)
      1465143808 blocks
       
md1 : active raid5 sdf1[3] sdo1[0] sdk1[1]
      3907022848 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      bitmap: 1/466 pages [4KB], 2048KB chunk

md127 : inactive sdq[8](S) sdi[11](S) sdg[6](S) sdr[2](S) sdh[10](S) sdn[4](S) sdl[12](S) sdj[7](S) sdb[0](S) sdd[5](S) sdc[9](S) sda[3](S)
      8790893568 blocks super 0.91


md1 is a raid5, but md126 and md127 are crap...  I don't know how this started, but it happens everytime I reboot.  Those disks in 126 & 127 belong to md0 which isn't started.  

So I do "mdadm --manage --stop /dev/md126" & 127...

Then I do "mdadm --assemble /dev/md0" and everything is good to go.  But it is annoying that everytime I reboot I have to remember to wait for it to boot so I can mess with this.

I checked the mdadm.conf file and it matches "mdadm --detail --scan".

I'm out of ideas...  anybody know what I can do next to fix this?

---

### Post by Kissell on 2011-05-29
Here is the detail of md0 after it starts, in case that helps.
NOTE: One drive died and I am waiting on a replacement drive to be shipped to me, but it is raid-6 so no big deal.  

Also, the raid not starting properly seemed to start happening after my upgrade to 11.04, but, it had been over three months since I rebooted before that, so I don't know if it is related or not.

"mdadm --detail /dev/md0"

> 
/dev/md0:
        Version : 0.90
  Creation Time : Tue Dec 30 07:24:07 2008
     Raid Level : raid6
     Array Size : 9523434752 (9082.26 GiB 9752.00 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 15
  Total Devices : 14
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May 29 22:12:12 2011
          State : clean, degraded
 Active Devices : 14
Working Devices : 14
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : 7257c8cd:2adbfa78:e9a9536a:3323098a
         Events : 0.1645207

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       97        1      active sync   /dev/sdg1
       2       8      145        2      active sync   /dev/sdj1
       3       8      209        3      active sync   /dev/sdn1
       4       8       17        4      active sync   /dev/sdb1
       5       0        0        5      removed
       6      65       17        6      active sync   /dev/sdr1
       7       8        1        7      active sync   /dev/sda1
       8       8       33        8      active sync   /dev/sdc1
       9       8      113        9      active sync   /dev/sdh1
      10      65        1       10      active sync   /dev/sdq1
      11       8      177       11      active sync   /dev/sdl1
      12       8      129       12      active sync   /dev/sdi1
      13       8      193       13      active sync   /dev/sdm1
      14       8      241       14      active sync   /dev/sdp1


---

### Post by ruffEdgz on 2011-05-30
I have a question that might sound silly but does your /etc/fstab show /dev/md0 as being a device to mount? If it does and the devices /dev/md126 and /dev/md127 are also on there, are they above or below /dev/md0?

It seems to me that the order in which the md devices are being mounted might be off? It's a shot in the dark without knowing a bit more about your setup.

---

### Post by Kissell on 2011-05-30
Neither array is in the fstab, only the system disk and the swap partition.

However, /dev/md1 is mounted just fine when I reboot, and /dev/md0 never is...  I have no idea where /dev/md126 and 127 are coming from.

---

### Post by ruffEdgz on 2011-05-30
This could be a risk but could you try removing both md126 and md127 from your system? It sounds like they are both created in /dev/md126 and /dev/md127 and if they aren't tied to anything, removing them should not be a problem.
```

mdadm --manage --remove /dev/md126
mdadm --manage --remove /dev/md127

```
Take this advise with a grain of salt as I also don't know where they came from or how your RAID config is actually setup. It just sounds like from this post that neither md126 or md127 are valued.

Also, could you display the output of the following commands (just curious how md0 is mounting if it isn't in the /etc/fstab):
```

sudo fdisk -l
cat /etc/fstab

```

Thanks and I can help later as I am going to bed for the night. I hope I can help out as much as I can while we are 13 hours apart ;)

---

### Post by Kissell on 2011-05-30
fdisk is long, I have 19 drives plus two multidisk arrays...  so I just listed the part related to md0...  

sudo fdisk -l
> 
Disk /dev/md0: 9752.0 GB, 9751997186048 bytes
2 heads, 4 sectors/track, -1914108608 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 1703936 bytes
Disk identifier: 0x08020000


cat /etc/fstab
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=761d081e-a1c2-48c4-bbed-b8fb74cea3ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=48c967f9-bd91-4291-90a9-3427517f5358 none            swap    sw              0       0


It isn't in fstab and yet it mounts, or at least it used to..  and md1 mounts...  I think this is because I added it to the /etc/mdadm/mdadm.conf file.  

Thanks for trying to help.  :) Good night.  :z

---

### Post by ruffEdgz on 2011-05-30
> It isn't in fstab and yet it mounts, or at least it used to.. and md1 mounts... I think this is because I added it to the /etc/mdadm/mdadm.conf file.

Yep, you are correct. Its been awhile since I have done my own software RAID on a computer since moving over to hardware RAID. I was thinking of the mounting of the /dev/md0 or /dev/md1 onto your system but the problem is the assembly of the array when starting up.

So in your mdadm.conf file, it is safe to say that you should have the DEVICES line and two ARRAY lines only? Does both of them use UUID to identify the ARRAY lines in that conf file? If you do have md126 and md127 around and you do the following command(s):
```

mdadm --detail --scan | awk '{print $2 " " $5}'

```
Are all the UUID's different or if you are using UUID's in your mdadm.conf file, are the correct values assigned to the correct arrays?

---

### Post by Kissell on 2011-05-30
> **ruffEdgz said:**
> Its been awhile since I have done my own software RAID on a computer since moving over to hardware RAID.

Yeah, this is an old project, started years ago when 750GB disks were the largest thing out there and hardware arrays were really expensive.  I'm just waiting until the 5TB drives come out, then I'm going to convert it to a four disk hardware raid array.

OK
**sudo mdadm --detail --scan | awk '{print $2 " " $5}'**
> 
/dev/md1 UUID=66f3aa88:5536bf0d:dbe25d4d:a8e2a3e1
/dev/md0


Oh NO!  No UUID?
**sudo mdadm --detail --scan**
> ARRAY /dev/md1 metadata=1.2 name=:Files UUID=66f3aa88:5536bf0d:dbe25d4d:a8e2a3e1
ARRAY /dev/md0 metadata=0.90 UUID=7257c8cd:2adbfa78:e9a9536a:3323098a


OK, what a relief.
**cat /etc/mdadm/mdadm.conf**
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
MAILADDR [email]Jeremy.M.Kissell@gmail.com[/email]

# definitions of existing MD arrays
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=66f3aa88:5536bf0d:dbe25d4d:a8e2a3e1
ARRAY /dev/md0 level=raid6 num-devices=15 UUID=7257c8cd:2adbfa78:e9a9536a:3323098a


# This file was auto-generated on Sat, 01 Jan 2011 09:54:03 -0600
# by mkconf $Id$


The UUIDs setup in mdadm.conf match the output of the detail scan of the arrays...  yet only md1 is loading.  And I have no idea where md126 and 127 are coming from.

---

### Post by Kissell on 2011-05-30
I found someone else having this problem.
[http://permalink.gmane.org/gmane.linux.raid/34028]("http://permalink.gmane.org/gmane.linux.raid/34028")

So I stopped md126 and md127 and assembled with the **mdadm -A /dev/md0 --update=super-minor** that it suggested.

Then I did the **update-initramfs -v -u** command and rebooted.

Now md126 has gone away and it has been replaced with an inactive md0 with only a few disks (the ones that were in md126).

However, md127 still exists and contains enough of the disks of md0 that md0 can't start.

So I repeated this process a few times, and nothing worked, no further progress.  Then I tried to update other parameters while assembling, but nothing worked.

BTW: When I do the detail scan when md127 is present, it doesn't see md127, I'll grab the exact output next time I reboot, but it didn't look like it would lead anywhere.

---

### Post by ruffEdgz on 2011-05-30
You can try and see if the command **dmesg** has any information about the md127 if it shows you when you boot up.
```

dmesg | grep -i md127

```
Its good that someone else has played around with this a bit more and had some information. I can take a look myself some more and see if I can reproduce it or see if updating anything else on the array can help.

---

### Post by Kissell on 2011-05-30
good idea, I completely forgot about dmesg, Ubuntu has been working so well for me for so many years. But, it didn't tell me anything useful.
> 
[  151.346604] md: md127 stopped.

The only information about md127 since I booted up is that I manually stopped it, in order to start md0.

---

### Post by ruffEdgz on 2011-05-31
Was looking around today some more about this and couldn't find anything outside from what you have tried back on [post #9]("http://ubuntuforums.org/showpost.php?p=10882235&postcount=9"). I did read an interesting blog about a person with the same problem but he removed the md127 and had some problems with his system:

[http://blog.siphos.be/2010/12/why-i-have-backups/](http://blog.siphos.be/2010/12/why-i-have-backups/)

It seems like the md127 might be tied in somehow to your md0 array (this just verifies your findings on post #9 once more).

As a temp solution though to this problem, maybe a script placed in the rcS.d directory could just run the two simple commands that you would need to do if a reboot was needed:
```

mdadm --manage --stop /dev/md127
mdadm --assemble /dev/md0

```
It isn't perfect but until you can redo the array or move it to a hardware raid controller server ;)

Keep in touch and best of luck with this.

---

### Post by Kissell on 2011-05-31
> **ruffEdgz said:**
> 
As a temp solution though to this problem, maybe a script placed in the rcS.d directory could just run the two simple commands that you would need to do if a reboot was needed:
```

mdadm --manage --stop /dev/md127
mdadm --assemble /dev/md0

```
It isn't perfect but until you can redo the array or move it to a hardware raid controller server ;)


Yeah, that's exactly what I did today.  LOL, problem solved!!! 

I have no idea why its doing what its doing, but for all intensive purposes, everything works with this workaround.  My desire to fix it properly isn't as strong as my desire to not entirely reinstall the OS.  This started about the time I upgraded to 11.04, and I had a problem where it hung during the end of the 11.04 upgrade and I had to reboot mid-upgrade...  I have a feeling if I reinstall the old version of linux from scratch that this will clear right up, but that's a lot of work for something that isn't really a problem anymore with this workaround.

---

### Post by santaslh on 2011-06-11
Try:
```

mdadm --stop /dev/md127
mdadm -A /dev/md0 --update=name
update-initramfs -vu

```

---

### Post by Kissell on 2011-06-12
> **santaslh said:**
> Try:
```

mdadm --stop /dev/md127
mdadm -A /dev/md0 --update=name
update-initramfs -vu

```

That didn't work for me.  However, I checked the version of mdadm, and the one that comes with maverick is old, so I updated to the latest stable v3.1.4 by downloading the deb from [http://packages.debian.org/sid/i386/mdadm/download]("http://packages.debian.org/sid/i386/mdadm/download") BAM!  Instantly fixed!  I went to stop md127 and assemble md0 after upgrading, and couldn't, 127 no longer existed and md0 was assembled properly.

---

