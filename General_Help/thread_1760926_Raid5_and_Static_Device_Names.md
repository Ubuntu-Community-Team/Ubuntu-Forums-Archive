---
title: "Raid5 and Static Device Names"
date: 2011-05-17
forum: General Help
---

### Post by NeilR on 2011-05-17
I am setting up a Raid5 and torture testing it.  I added two eSata ports to my machine.  When a drive is installed in that eSata port and the machine then booted up the device name (e.g. /dev/sdc) is inserted in the middle of my Raid devices.  And that is just one example of how the device names can change.

I did a search on 'static device names' but I saw nothing directly related to Raid.  What I did see were suggestions to create udev rules based on UUID.  But that was for single disks, not Raid, where each drive/partition in the raid array appears to have the same UUID.

I'm surprised this does not come up in the various Raid howtos because it is impossible to keep a Raid array intact without solving this problem unless the machine is never touched thereafter.

Any suggestions would be appreciated!

---

### Post by YesWeCan on 2011-05-17
> **NeilR said:**
> I am setting up a Raid5 and torture testing it.
Getting your own back? :P

Are you talking about mdraid? I have always used UUIDs. They are specified in /etc/mdadm/mdadm.conf:

```
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
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=86779d62:ae742571:adb101fa:93741ce9
ARRAY /dev/md0 level=raid10 num-devices=4 UUID=f3c98c9c:74235cf2:6ded50c4:977e48b4

# This file was auto-generated on Thu, 13 Jan 2011 18:42:19 +0000
# by mkconf $Id$
```

---

### Post by PavelMan on 2012-04-30
This is SO true! I do not know if you were ever abl to solve the puzzle, but I have burnt a few times on this already, before I have figured out what is going on.

When I insers a USB drive, it is mounted as /dev/sdd, but it you reboot with it still plugged in, it becomes /dev/sdb, which is a part of raid! And this automatically fails and excludes one disk. More that that, I can not even --re-add the sdd1, which is now one of the former raid array members.

And yes, the ARRAY is mdconf has the UUID, but it is the UUID if the whole array (/dev/md127 in my case, which is another famous glitch).

So I have to be VERY careful now to not reboot with a USB drive plugged in, or is screwes up the raid5. 

If anybody can pont me to the right direction - that would be awesome! As this is the most releval post I have found so far ;-).

---

### Post by CharlesA on 2012-04-30
Use the UUID instead of the device name if you don't want to run into problems later.

As for the UUID listed in mdconf, that would be the UUID of the array. You can verify that by running this:

```
sudo blkid -c /dev/null
```

---

### Post by PavelMan on 2012-04-30
Thanks for your response, CharlesA. Where do you suggest using UUIDs? This is what I have in /etc/mdadm/msadm.conf:

ARRAY /dev/md127 level=raid5 num-devices=3 metadata=1.2 UUID=561f703f:9865e08d:0fbb4f5c:2e454cc4 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1

Are you saying I can use UUID instead of /dev/sd[b,c,d]1 ? This is what blkid is saying (wow, I guess I have messed up the configuration more than I thought I did ;-) ).

> ubackup@anubis:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="98c8c3fe-06c9-4431-9d9f-6afe2db75c67" TYPE="swap"
/dev/sda5: UUID="922b1686-82e8-4e51-baf4-19c4d58c88a5" TYPE="ext4"
/dev/sdb1: UUID="561f703f-9865-e08d-0fbb-4f5c2e454cc4" UUID_SUB="923fa2cd-9af7-265b-ec65-62583a2ff1e9" LABEL="anubis:0" TYPE="linux_raid_member"
/dev/sdc1: UUID="561f703f-9865-e08d-0fbb-4f5c2e454cc4" UUID_SUB="c4fc73f4-a7f9-086a-13b6-a01b6099a043" LABEL="anubis:0" TYPE="linux_raid_member"
/dev/sdd1: UUID="561f703f-9865-e08d-0fbb-4f5c2e454cc4" UUID_SUB="8f6ed70d-adbb-6256-b8db-0b0996604757" LABEL="anubis:0" TYPE="linux_raid_member"
/dev/md127: UUID="56c695ca-8c77-4e88-b959-f383b3ce1050" TYPE="ext3"
ubackup@anubis:~$


---

### Post by CharlesA on 2012-04-30
I meant just use the UUID when you are mounting the array using something like fstab.

You wouldn't be able to use the UUID for the device names in mdadm because that is the UUID of the entire array not each individual disk.

---

### Post by PavelMan on 2012-04-30
I am not sure I understand what it has to do with /dev/sd... getting shuffled around on re-boot.

My fstab has the following in it

```
/dev/md127 /home/ubackup/Raid  ext3  defaults 0  0
```

And I can replace /dev/md127 with some UUID (I guess, it should be 56c695ca-8c77-4e88-b959-f383b3ce1050, even though I am not sure why is is different from what I have in mdadm.conf, I guess it is a "drive" or ARRAY vs. "rartition" type of difference).

But, /dev/sdb, sdc, etc. will still exist. And when USB drive will be plugged in, upon rebboot, it will still bump one of hard drives out of their /sdX position, which will ruin the assembly of the raid5 array.

And, even though the mounting in fstab will be done correctly, regardless of this being /dev/md0, /dev/md127 or /dev/md/anubis:0 - the array will still go into degrade state with one drive excluded...

Please, tell me you have the solution in mind, and I just do not understand it ;-).

---

### Post by rubylaser on 2012-04-30
mdadm does not just assemble the devices in the order that they are in the system (/dev/sdX) unless you explicitly tell it to use those disks.  It uses the UUID in the superblock on each disk.  I'd like to see the output of these two commands.

What's the output of this?
```
mdadm --detail /dev/md127
```
```
cat /proc/mdstat
```

You need to change your change your mdadm.conf file to get this working correctly. Finally to get this fixed, here's what you need to do.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

It's currently degrading because when you operate with the USB drive attached, one of your disks is moving to /dev/sde1 and since your mdadm.conf tells it to only use /dev/sd[abcd]1, it's degraded.

Finally, update your initramfs for good measure.
```
update-initramfs &#8211;k all &#8211;u
```

---

### Post by PavelMan on 2012-04-30
Thanks rubylaser, I think we are onto something! I have heared similar suggestions before, but not an exact this one. 

After unplugging the usb drive and rebooting, I have got my sd[b,c,d]1 back, but the array still was in a degraded state, despite no writes...i believe... were made to it in-between. And I could not --re-add /dev/sdd1 no matter what I tried. So I have just zeroed the superblock on it and did --add. So, it is rebuilding now. But I very much want to get to the bottom of this problem, so it never happens in the future to me or other fellow software-raiders.

sudo mdadm --detail /dev/md127:
```

/dev/md127:
        Version : 1.2
  Creation Time : Thu Apr 26 18:32:55 2012
     Raid Level : raid5
     Array Size : 1953520640 (1863.02 GiB 2000.41 GB)
  Used Dev Size : 976760320 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Apr 30 22:37:05 2012
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 96% complete

           Name : anubis:0  (local to host anubis)
           UUID : 561f703f:9865e08d:0fbb4f5c:2e454cc4
         Events : 4717

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      spare rebuilding   /dev/sdd1
```
sudo cat /proc/mdstat:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid5 sdd1[3] sdb1[0] sdc1[1]
      1953520640 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
      [===================>.]  recovery = 99.1% (968462404/976760320) finish=4.1min speed=33346K/sec
```

Here is what I do not understand here - why is sdd1 having [3] next to it? I swera I was using mdadm --create with /sdb1, /sdc1. /sdd1 at the end...

Here is what my mdadm.conf has now:
```
DEVICE /dev/sd??
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR myactualaddress@myactual.domain
ARRAY /dev/md127 level=raid5 num-devices=3 metadata=1.2 UUID=561f703f:9865e08d:0fbb4f5c:2e454cc4 
```
the last line before the reboot was saying 
```

ARRAY /dev/md/anubis:0 level=raid5 num-devices=3 metadata=1.2 name=anubis:0 UUID=561f703f:9865e08d:0fbb4f5c:2e454cc4
   devices=/dev/sdb1,/dev/sdc1,/dev/sdd1 
```
I have adjusted it in the process of trying to figure it out ... and did the ```
 update-initramfs -u
```
I did not use "-k all" option, though (I do not know what it is ;-) ).
And, I have heared, that even among those /dev/sd[b,c,d]1 - there is no guarantee the actual order of physical drives it maintained every time you reboot. So, I am thinking of starting to mess with "udev", but I know too little about it at this point, which makes me hesitate a bit ;-). Any advice is appreciated!

---

### Post by rubylaser on 2012-05-01
It has a 3 next to it because you "removed" the old disk (2) and so it's taken on the (3) role number.

I would set my mdadm.conf up like this.
```
DEVICE partitions
HOMEHOST <system>
MAILADDR myactualaddress@myactual.domain
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=1.2 UUID=561f703f:9865e08d:0fbb4f5c:2e454cc4
```

mdadm is smart enough to assemble you array from the UUID's stored on each disk's superblock. There's really no reason to list /dev/sd?? at all.  Also, I would change the md device to /dev/md0 as that's the standard format for your first md device (you'd need to modify /etc/fstab to coincide with that change).

> And, I have heared, that even among those /dev/sd[b,c,d]1 - there is no guarantee the actual order of physical drives it maintained every time you reboot. So, I am thinking of starting to mess with "udev", but I know too little about it at this point, which makes me hesitate a bit . Any advice is appreciated!

You don't have to worry about the physical order of the drives.  mdadm is really smart, and doesn't need the disks to be in the same order.  As long as your mdadm.conf file isn't limiting it, it will assemble the disks automatically for you irregardless of the order that the OS presents them. So, you don't have to worry about this part. You can view each disk's UUID and superblock info like this to see what I mean.

```
mdadm -E /dev/sd[bcd]1
```

---

### Post by PavelMan on 2012-05-01
rubylaster, rigt before your post this morning I have checked the status, resyncing was done, so I have restarted to see what happens. The mdadm.conf I used (plus "update initramfs -u" after the change) was 

```
DEVICE /dev/sd??
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR myactualaddress@myactual.domain
ARRAY /dev/md127 level=raid5 num-devices=3 metadata=1.2 UUID=561f703f:9865e08d:0fbb4f5c:2e454cc4
```

So, it was, in fact, very close to what you are recommending. And I have actually started with /md0, just like a normal person would, but for some reason every time after the reboot md0 kept diappearing, and md127 was present ;-). So the array would not mount. So, I thought "well, if you like md127 so much - let it be it". And it even worked once,...I think... . But ever since the USB drive was left in on reboot - it is a mess...

So, after the reboot, I've got...
```
ubackup@anubis:~$ sudo mdadm -D /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Thu Apr 26 18:32:55 2012
     Raid Level : raid5
     Array Size : 1953520640 (1863.02 GiB 2000.41 GB)
  Used Dev Size : 976760320 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue May  1 13:26:55 2012
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : anubis:0  (local to host anubis)
           UUID : 561f703f:9865e08d:0fbb4f5c:2e454cc4
         Events : 4733

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed
```
Q1: can i re-add sdd1? I mean ... I do not mind wasting another 8 hours and do the regular add, but re-add would be so much nicer! Becides - isn't it the whole purpose of it? but ```
ubackup@anubis:~$ sudo mdadm /dev/md127 --re-add /dev/sdd1
mdadm: --re-add for /dev/sdd1 to /dev/md127 is not possible
```

Then, another misterious thing is that sudo fdisk -l says I have a non-standard chunk 4096, while I swear I've never done this on this machine. mdadm --create was ran without any chunk specification, so the default 512 should be in place. And this is what mdadm -D above shows. But fdisk... (have plugged in the offending disk now, after the reboot, so it became sde, to take all the data off the box ;-). It is not much, about 1T of backups, but I still do not want to loose them, as it is the only backup copy I have for my other servers... 

```
ubackup@anubis:~$ sudo fdisk -l
[sudo] password for ubackup:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c16b085

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3905535     1951744   82  Linux swap / Solaris
/dev/sda2         3907582   312580095   154336257    5  Extended
/dev/sda5         3907584   312580095   154336256   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
78 heads, 63 sectors/track, 397542 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93c6590d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953525167   976761560   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
60 heads, 63 sectors/track, 516805 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8348440b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953525167   976761560   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
36 heads, 63 sectors/track, 861342 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc42ca6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953525167   976761560   fd  Linux raid autodetect

Disk /dev/md127: 2000.4 GB, 2000405135360 bytes
2 heads, 4 sectors/track, 488380160 cylinders, total 3907041280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table
Note: sector size is 4096 (not 512)

Disk /dev/sde: 3000.6 GB, 3000592965632 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566642 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4aae0a0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   732564062  2930256000    7  HPFS/NTFS/exFAT
```

So, the "runaway" sdd1 is now [2], but listed as "removed" ```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid5 sdb1[0] sdc1[1]
      1953520640 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
```
 
I do not know what is going on. It feels like there are some more settings somewhere, which are "remembered" from all these previous attempts, and who knows what they are now. maybe this is the -k all switch for the update-initramfs? I will look into this...

I was so fond of the mdadm software raid idea, that I wanted to switch another backup server from the 32-bit Win 2008 to Ubuntu, with 2TBx4 raid5 with 1 spare. The box does not have a CD-rom, so I have even cooked the usb flash drive with 12.04 server on it... So, I need to get to the bottom of it, really, as I may start having problems with the new install off the bat, right after I pull the usb installation flash out... unless the system make a difference between "flash" media and "actual hard drives in a box, but still plugged through usb"...
At the moment I am a bit puzzled...
Honestly, it is superstrange

---

### Post by rubylaser on 2012-05-01
Do you have data on this array already?  If not, personally I would zero the superblocks on each of these disks, then I would write zeros to each of the disks to remap any bad sectors, then I would start over with a fresh array.

If you do have data on there, you need to figure out why your disk keeps getting kicked out of the array.  I'd run a long smart test on all of your disks and make sure they all pass, and don't have UDMA_CRC errors (bad SATA cable).  Also check dmesg, the disk being kicked out of the the array should show up there.

The -k flag won't fix this problem.  One of your disks is being kicked out of the array.  It's either got a bad cable, bad motherboard head, bad drive, or the drive is taking too long to respond.

Finally, the reason you had /dev/md127 is the ARRAY statement in mdadm.conf needs to be correct. 
Minimizing the specifiers in your ARRAY statements: all you normally need is device name and UUID.    So your array line really can be as simple as this.
```
ARRAY /dev/md0 UUID=561f703f:9865e08d:0fbb4f5c:2e454cc4
```

This [post]("http://ubuntuforums.org/showpost.php?p=11452217&postcount=20") explains the problem with metadata 1.2.

---

### Post by PavelMan on 2012-05-03
I have decided to give it a try - convert yet another machine to ubintu server 12.04 It has larger drives, so the process of building a raid is going to take much longer. And I wll try a very parsimonious mdadm.conf line, just as you suggest - 
```

#DEVICE partitions containers
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR myname@domain.org
ARRAY /dev/md0 UUID=953a0832:59d3922f:c3b7e12c:0dda0868

```

The strange thing here, is that this is the default file + the ARRAY statement. in 11.04 there was an actual DEVICE statement under the commented-out part. In this one (fresh, installed yesterday) - nothing is there for DEVICE. I wonder how important is it to have something there before I restart.

When making partitions, I have tagged them with "fd". So here is my fdisk -l:
```


Disk /dev/sda: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f05d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   118007807    59002880   83  Linux
/dev/sda2       118007808   120102911     1047552   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
164 heads, 44 sectors/track, 541439 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005d305

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3900704767  1950351360   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
164 heads, 44 sectors/track, 541439 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e5f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3900704767  1950351360   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
164 heads, 44 sectors/track, 541439 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d5ba2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3900704767  1950351360   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 2500.5 GB, 2500495958016 bytes
164 heads, 44 sectors/track, 676798 cylinders, total 4883781168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3900704767  1950351360   fd  Linux raid autodetect

Disk /dev/md0: 3994.3 GB, 3994316439552 bytes
2 heads, 4 sectors/track, 975174912 cylinders, total 7801399296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

And this will be a raid6 array, as I do not want to feel horrible and rushed every time a drive pops out for unknown reason, especially while experimenting.

Here is my /proc/mdadm:

```

Personalities : [raid6] [raid5] [raid4]
md0 : active raid6 sde1[3] sdd1[2] sdc1[1] sdb1[0]
      3900699648 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]
      [=================>...]  resync = 86.0% (1677513996/1950349824) finish=152.2min speed=29857K/sec

```

So, am I ready for a successful restart this way? I will wait until it is all done, and make the file system for /md0, but other than that - will I have a 100% healthy array after reboot? (no flash drives plugged in SO FAR, but I bet I will at the next step!).

Thanks everyone looking at this excersise, I am sure it will make the world a bit better ;-).

---

