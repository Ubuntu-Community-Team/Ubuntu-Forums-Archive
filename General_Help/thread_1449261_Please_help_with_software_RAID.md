---
title: "Please help with software RAID"
date: 2010-04-07
forum: General Help
---

### Post by Mindgamer on 2010-04-07
Hope someone can help me - I am trying to create a RAID data drive for my system but I am having setting it up since I am a total linux noob.

The system has 3 physical HDD-s:
1. 320 GB (has functional Ubuntu 9.10 installation) attached to a PCI SATA card
2. 2TB on motherboard
3. 2TB on PCI SATA card

I want to create a software RAID1 of disks 2 and 3. So far I have used the Palimpsest Disk Utility:
- Created a GUID Partition table on both disks (2, 3)
- Used File -> New -> Software Array, made sure both my drives were included
- Once Palimpsest listed the RAID Drive as a Software RAID Array, I told it to create Ext3 filesystem on it

Well.. at least thats what I thought I did. At this point I have been able to mount the RAID drive and put files on it. However when I look at its information in Palimpsest, I am told that the drive is not partitioned. Both RAId components /dev/sda1 and /dev/sdc1 are reported to be in Sync, but the RAID Drive's own state is 'Running, Resyncing @ 45%' (and lowly growing). 

My questions are:
Is this a normal setup or did I do something incorrectly? Why is the drive reporting to have no partition? And howcome I can use it if it does not have a partition? I have found the command line based configurations to be a tad too confusing to follow, so I have tried to stick to graphical tools - is this a hopeless cause in Ubuntu or is it possible to achieve what I want to do without command line?

I will list some info on my disks below - perhaps this offers more insight to those of you more familiar with Linux.

Thank you.

```
mindgamer@mind-server:~$ sudo lshw -C disk
[sudo] password for mindgamer: 
  *-disk:0                
       description: ATA Disk
       product: WDC WD3200BEVT-0
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WX31A1xxxxxx
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0006xxxx
  *-disk:1
       description: ATA Disk
       product: WDC WD20EARS-00S
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 80.0
       serial: WD-WCAVY2xxxxxx
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=b583a606-xxxx-xxxx-xxxxx-7994ddxxxxxx
  *-disk
       description: ATA Disk
       product: WDC WD20EARS-00S
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 80.0
       serial: WD-WCAVY2xxxxxx
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=c246e9ca-xxxx-xxxx-xxxx-2f660e3xxxxx
mindgamer@mind-server:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066496

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38167   306576396   83  Linux
/dev/sdb2           38168       38913     5992245    5  Extended
/dev/sdb5           38168       38913     5992213+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514583+  ee  GPT

Disk /dev/md0: 2000.4 GB, 2000398778368 bytes
2 heads, 4 sectors/track, 488378608 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by Mindgamer on 2010-04-08
So... the syncing is now complete - i guess it was supposed to take this long. 

However the RAID disk is still reported to have no partition. Is this normal?

---

### Post by prodigy_ on 2010-04-08
I think you need to read [https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID]this part of the RAID HOWTO](https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID]this part of the RAID HOWTO).

Anyway, can you access your /dev/md0? I mean - can you, for example, create a file there?

---

### Post by Mindgamer on 2010-04-12
> **prodigy_ said:**
> I think you need to read [this%20part%20of%20the%20RAID%20HOWTO"]https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID]this part of the RAID HOWTO]("https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID).

Anyway, can you access your /dev/md0? I mean - can you, for example, create a file there?

Thanks for the link - some real good info there. I decided to try an make everything from scratch, following the instructions on that page. (just to answer your question - yes I was able to write files to the disk)

1. sudo fdisk /dev/sda (created primary partition with id fd)
2. sudo fdisk /dev/sdc (created primary partition with id fd)
3. sudo mdadm --create --auto=mdp --verbose /dev/md_d0 --level=mirror --raid-devices=2 /dev/sda /dev/sdc (It ran over the night, syncing the disks)
4. sudo mkfs -t ext3 /dev/md_d0p1

At this point I felt pretty good about everything. I mounted the disk doing:
1. sudo mkdir /media/datadisk1
2. sudo mount /dev/md_d0p1 /media/datadisk1

The disk got mounted in the Media folder. However I was unable to write any files to it. Thinking a reboot has ALWAYS helped me before, I rebooted the machine and decided to check the drive again then. Of course as I logged on it turned out I would have to assemble the RAID again manually before I could mount it.

However when I do:
sudo mdadm --assemble /dev/md_d0 /dev/sda1 /dev/sdc1
I get the error "no recogniseable superblock on /dev/sda1"
ARGHHH

Thinking unhappily that I will have to do the whole RAID building again, I attempt to start up the RAID drive from Palimpsest and to my surprise it works! However I am still unable to write any files to the drive. Using 'sudo chmod 666 /media/datadisk1' didnt help me.

I would like to ask:
- Did I mess up something? Why cant I assemlble the array from CLI?
- Any advice on how to make the drive usable?
- Any advice on how to make the array assemble and mount itself automatically at boot?

Thanks

Edit: Oh right.. some info from commands just in case:
```
mindgamer@mind-server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda[0] sdc[1]
      1953514496 blocks [2/2] [UU]

unused devices: <none>

mindgamer@mind-server:~$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb6dc486

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066496

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38167   306576396   83  Linux
/dev/sdb2           38168       38913     5992245    5  Extended
/dev/sdb5           38168       38913     5992213+  82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb6dc486

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000398843904 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb6dc486

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      243201  1953512001   fd  Linux raid autodetect

```

---

### Post by prodigy_ on 2010-04-12
Hmm. I don't see anything wrong about the commands you use. Try ```
mdadm --examine /dev/sda1
``` Maybe it'll give more info.

---

### Post by Mindgamer on 2010-04-12
> **prodigy_ said:**
> Hmm. I don't see anything wrong about the commands you use. Try ```
mdadm --examine /dev/sda1
``` Maybe it'll give more info.

1. The drive is still mounted (succeeded with Palimpsest) and I get:
```
mindgamer@mind-server:~$ sudo mdadm --examine /dev/sda1
mdadm: cannot open /dev/sda1: No such file or directory
```2. I do a reboot of the system

3. Now I get:
```
mindgamer@mind-server:~$ sudo mdadm --examine /dev/sda1
[sudo] password for mindgamer:
mdadm: No md superblock detected on /dev/sda1.
```Palimpsest reports:
0.0 KB RAID-1 Drive
0.0 KB Software RAID
RAID Array
In the right hand details section:
Unknown Size
Unrecognized
Linux Software RAID
/dev/md_d0
Array Name: -
Home Host: -
Array Size: -
RAID Type: Mirrored (RAID-1)
Components: 2 Components (2000 GB each)
State: Not running, partially assembled
Nothing is listed in the RAID components screen.

I have the option to stop the RAID array from Palimpsest. As I did this, on the left hand 'Drive tree' appared a new branch with:
RAID device /dev/md_d0 ()
0.0KB Software RAID

Completely confused once again I reboot the system and hope someone smarter has a better idea of what is happening :) (After reboot the 'new branch' is gone, everything else is the same). From Palimpsest no option to start up or mount the drive - only option is 'stopping' it again.

---

### Post by misterbk on 2010-04-12
Too bad I don't still have my CentOS RAID box up and running...

I remember a few things from that experience though:

- I had to run hdparm on the individual drives to turn off write caching.  Think it was due to a bug.  The system would freeze up for 3 to 10 seconds when there was write activity, spit something cryptic into the logs, then resume as if nothing had happened.

- The individual drives were still visible after creating the raid.  Creating the raid added a new device /dev/md0 but /dev/sda,b,c,d,e,f,g,h didn't go away.

- In my setup, I created two partitions on all 8 disks, one for making a raid0 and one for making a raid1.  I created the RAID volume on the partitions and not the disks.  (i.e. using /dev/sda1, sdb1, sdc1 etc, not /dev/sda, sdb, sdc)

- I had to use a GPT partition table because it was a 4TB Raid10.  That meant I could not use fdisk.  Maybe parted would report things differently?  I don't even know for sure if fdisk supports md volumes.

Edit:  I don't know for sure, i.e. GPT might be mandatory for software RAID, but it looks like you do not actually have to use GPT.  Your disks are 2TB each, GPT is necessary for volumes greater than that.  Your soft Raid-1 would also be 2TB.  It appears that you are using GPT though so use parted and not fdisk.

---

### Post by Mindgamer on 2010-04-25
I got my raid up and running.. sort of. I am still not 100% on how fail-safe it is or how to retrieve the data when one disk fails. I will try to get that part sorted in another thread. But for now the raid seems to be ok.. it gets assembled and mounted at startup... I have shared it out as a samba share and can write and read data to it from my windows machine. As I want to grow the array in the future as comfortably as possible and LVM seemed to be the way to go ... I use that.

For anyone interested, I will put here how I created the array...
All critique and advice is very welcome.

1. sudo fdisk /dev/sda
 Used Linux LVM (8e)... repeat for disk /dev/sdc

2. sudo mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 /dev/sda1 /dev/sdc1

3. sudo mdadm --detail --scan
Then used the displayed data to update mdadm.conf:
sudo gedit /etc/mdadm/mdadm.conf
Added this line:
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=0.90 UUID=95203a87:82ac37f2:bcfb3cd7:b9f19abc

4. sudo fdisk /dev/md0
Used Linux LVM (8e)

5. Made LVM physical volume: sudo pvcreate /dev/md0

6. Created LVM volume group: sudo vgcreate fileserver /dev/md0

7. Created Logical colume: sudo lvcreate -l 476931 fileserver -n volume1

8. Created filesystem: sudo mkfs.ext3 /dev/fileserver/volume1

9. Mounted filesystem: sudo mount /dev/fileserver/volume1 /media/raidmd0

10. Gave ownership to user mindgamer

11. sudo gedit /etc/fstab
Added automount:
/dev/fileserver/volume1 /media/raidmd0 auto defaults 0 0

---

