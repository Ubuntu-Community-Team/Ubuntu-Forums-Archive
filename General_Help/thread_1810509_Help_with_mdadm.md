---
title: "Help with mdadm"
date: 2011-07-23
forum: General Help
---

### Post by imhotep531 on 2011-07-23
I have the following SATA drives connected to my machine:

/dev/sda 80GB
/dev/sdb 500GB
/dev/sdc 500GB

/sdb and /sdc are not formatted and I'm trying to set them up as RAID 1 using mdadm.  They are connected to a PCI-E card with two SATA II ports.  The card also provides fakeRAID.

When I run this command:

sudo mdadm -C /dev/md0 -l 1 -n 2 /dev/sdb /dev/sdc

I get this error:

[B]mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: Cannot open /dev/sdc: Device or resource busy[/B]

I have tried a couple of things.  [This thread]("http://www.righteoushack.net/?p=197") says the onboard fakeRAID features could be interfering, so I entered the card's BIOS and made sure no arrays were in existence.  Then I uninstalled dmraid.  This did not work.

Next I read [this thread]("http://blog.itsfortytwo.net/2010/08/ubuntu-mdadm-device-or-resource-busy-error/") but he's already successfully created the array and his problem was that it disappeared after restarting.  I can't even create the array in the first place.

Any ideas?  Thanks for your help.

---

### Post by Habitual on 2011-07-23
Here's part of a cookbook recipe I did for my raid0 experience last week using an instance at AWS.

Maybe it will help. 
```

apt-get install -y mdadm xfsprogs
mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
mkfs.xfs -d sunit=512,swidth=2048 /dev/md0
mkdir -v /mnt/raid1
mount /dev/md0 /mnt/raid1/

df -h
/dev/md0               40G   33M   40G   1% /mnt/raid1

```
# now scan/exmaine and add to the /etc/mdadm/mdadm.conf
```

mdadm --examine --scan --config=/etc/mdadm/mdadm.conf
mdadm --examine --scan --config=/etc/mdadm/mdadm.conf >> /etc/mdadm/mdadm.conf

```

```
vi + /etc/fstab
``` and add
```
/dev/md0 /mnt/raid1 xfs defaults 0 0
```

adjust /mnt/raid1 to your desired mounted directory.

some useful commands I found were:
```
mdadm --detail /dev/md0
cat /proc/mdstat
umount /dev/md0
mdadm --stop /dev/md0

```

Please let us know...

---

### Post by imhotep531 on 2011-07-23
Habitual,

When I run mdadm it simply says:

mdadm: failed to create /dev/md0

So I run the second line of your code as root, and this is the output I receive:

sudo mdadm --create --verbose /dev/mdo --level=1 --raid-devices=2 /dev/sdb /dev/sdc
mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: /dev/sdc appears to be part of a raid array:
     level=raid1 devices=2 ctime=Wed Jul 20 20:24:27 2011
mdadm: create aborted

What next?

---

### Post by coffee412 on 2011-07-23
> **imhotep531 said:**
> Habitual,

When I run mdadm it simply says:

mdadm: failed to create /dev/md0

So I run the second line of your code as root, and this is the output I receive:

sudo mdadm --create --verbose /dev/mdo --level=1 --raid-devices=2 /dev/sdb /dev/sdc
mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: /dev/sdc appears to be part of a raid array:
     level=raid1 devices=2 ctime=Wed Jul 20 20:24:27 2011
mdadm: create aborted

What next?

Saw your thread and thought I could help you out. I dont mean to butt in.

First thing is first, Fire up a term window and run fdisk on both drives. Remove all partitions and then write changes to disk. Then with fdisk create one new partition on each drive. Change the partition type to "fd" as a linux raid partition. Now write the changes to disk and exit fdisk.

Now you will be setting up a raid 1 array using mdadm:

> mdadm --create /dev/md0 --level=raid1 --force /dev/sdb1 /dev/sdc1After it is created you can then create your mdadm.conf file like this:

> mdadm --detail --scan --verbose > /etc/mdadm.confThen format the array (/dev/md0) and mount it. Make the changes to your /etc/fstab so that it mounts on reboot.

Pay special attention to the partitions of the drives. They are NOT /dev/sdb , /dev/sdc but ARE /dev/sdb1 /dev/sdc1

Hope this helps.

coffee

---

### Post by imhotep531 on 2011-07-23
coffee, thank for your help.  Ok a ran through the steps you listed using fdisk.  I created a new partition on each drive and set the partition type to 'fd', then wrote the tables to disk and quit fdisk.  All of that seemed to work perfectly.

When I got to run the first mdadm code you gave, I get this:

sudo mdadm --create /dev/md0 --level=raid1 --force /dev/sdb /dev/sdc
mdadm: no raid-disks specified

I'm really confused because I set them both to be 'fd' with fdisk.  Thanks again for your help.  Any other ideas?

---

### Post by imhotep531 on 2011-07-23
Sorry there was a typo in my last reply.  This is actually what I typed, adding the '1' to each disk name:

sudo mdadm --create /dev/md0 --level=raid1 --force /dev/sdb1 /dev/sdc1
mdadm: no raid-disks specified

---

### Post by coffee412 on 2011-07-23
Run this in a term window and post the output ok?

fdisk -l

btw -- try changing the id to 83. That is what my raid5 with 4 320 giggers show.

sorry.

---

### Post by imhotep531 on 2011-07-23
Unfortunately I'm running Ubuntu Server 10.04.2 on its own machine and I'm using a laptop with Windows 7 to post on this forum, so I don't have a way to copy/paste all the output of fdisk -l.  I can tell you specific details though if I know what you are wanting to check.  Thanks for sticking with me!

---

### Post by coffee412 on 2011-07-23
> **imhotep531 said:**
> Unfortunately I'm running Ubuntu Server 10.04.2 on its own machine and I'm using a laptop with Windows 7 to post on this forum, so I don't have a way to copy/paste all the output of fdisk -l.  I can tell you specific details though if I know what you are wanting to check.  Thanks for sticking with me!

I can hang a while and work on this. I did make a mistake about the partition type. Change it to type 83

/dev/sda1   *           1       38913   312568641   83  Linux

Thats my first raid drive. I run 4 seagate 320 gig disks setup as a raid5. Notice the partition type is 83 not fd.

---

### Post by imhotep531 on 2011-07-24
Ok here are the highlights from fdisk -l.  I have combined them into a single table even though they appear in the output under their respective physical drives, if that makes sense.

Device        Boot        Start        End        Block            Id        System
/dev/sda1    *            1            4864        39061504        83    Linux
/dev/sda2                4864        4985        975873          5        Extended
/dev/sda5                4864        4985        975872          82    Linux swap / Solaris
/dev/sdb1                1            191412    488385560       83    Linux
/dev/sdc1                1            191412    488385560    83    Linux

---

### Post by coffee412 on 2011-07-24
> **imhotep531 said:**
> Ok here are the highlights from fdisk -l.  I have combined them into a single table even though they appear in the output under their respective physical drives, if that makes sense.

Device        Boot        Start        End        Block            Id        System
/dev/sda1    *            1            4864        39061504        83    Linux
/dev/sda2                4864        4985        975873          5        Extended
/dev/sda5                4864        4985        975872          82    Linux swap / Solaris
/dev/sdb1                1            191412    488385560       83    Linux
/dev/sdc1                1            191412    488385560    83    Linux


As far as I can see things should start working now. Try creating your raid and lets see what happens. 

Hummm. Here is a nice post on setting up raid that you can pull some more info from. 

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)


coffee

---

### Post by imhotep531 on 2011-07-25
Sorry I guess was a little vague.  It is not working even with everything set up as shown in the fdisk -l output.  I am getting the error stating that no raid devices were selected.

Gotta say command line is pretty counter-productive at first.  I've been spinning my wheels for about a week now.  I don't consider myself a purist so I'm very tempted to stop wasting time and install the GNOME desktop on this server so I can use the included utilities more quickly.  Before I do that I'm going to wipe this installation and start over, give it one more try.  I'm now reading through [this book]("http://www.amazon.com/Practical-Guide-Ubuntu-Linux-3rd/dp/013254248X/ref=sr_1_1?ie=UTF8&qid=1311598800&sr=8-1") to get a better understanding of Ubuntu as a whole instead of nit picking the individual tasks I'd like to complete, such as RAID.

---

### Post by coffee412 on 2011-07-25
One thing is that most of the raid documentation out there is getting old. Alot of it deals with the old raid setups that really are no longer used as far as software raid goes. Dont give up the ship yet though. I wouldnt wipe your current setup. Im sure we can get this thing going. Let me google some more information and Ill post back in just a bit.

coffee

---

### Post by coffee412 on 2011-07-25
Lets try something first. According to the docs your individual raid members should be fd (auto raid detect). Therefore, Lets get that set back to where it should be. 

Perhaps the system is not reading the new partition settings. This could be part of your problem. Therefore after doing the above lets have the system re-read the partition tables with the command below:

> partprobe

Now lets try and assemble the raid again:

> mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

Let me know if this worked.

coffee

---

### Post by imhotep531 on 2011-07-25
Ok I used fdisk to change /dev/sdb and /dev/sdc back to 'fd'.  I confirmed the change with 'fdisk -l' and I see that /dev/sdb1 and /dev/sdc1 are both now listed as 'fd'.

When I run partprobe, I get a series of responses that look like this:

[   165.358250]   end_request: I/O error, dev fd0, sector 0

It goes on and on like that, except the first number in brackets changes.  At one point the list of responses like this one is interrupted by a single line that says:

Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

I'm not even sure what fd0 is because I have never used this name myself to create anything.  I tried to create /dev/md0 awhile back but it consistently fails.

---

### Post by coffee412 on 2011-07-25
> **imhotep531 said:**
> 

When I run partprobe, I get a series of responses that look like this:

[   165.358250]   end_request: I/O error, dev fd0, sector 0

Warning: Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

I'm not even sure what fd0 is because I have never used this name myself to create anything.  I tried to create /dev/md0 awhile back but it consistently fails.


That is the device name for a floppy disk drive. Obviously you do not have one but the bios probably is setup to one. Therefore it cannot access it and gives the errors. So, You can ignore those errors.

Im assuming you are still getting the "Raid devices not available" error still. Interesting...

Reinstalling will not fix anything best to slowly work on the problem and get it resolved. I will post more in a bit with more ideas.

One thing to check. Go into your bios on the computer and see if the drives are setup as AHCI devices or IDE. I would make sure they are IDE and try again to create the raid device.

Well get it. Sooner or later...
:)

---

### Post by imhotep531 on 2011-07-27
I've been trying to work on this again but haven't had time the past couple of days.  I'm going to try again tonight.

I am wondering if my SATA card may be confusing Ubuntu.  I go into the card's BIOS and make sure no arrays were in existence, but the BIOS doesn't have an ON/OFF setting for RAID.  Rather you can delete any existing arrays and it will only list the drives individually.  So that's what I did but I wonder if Ubuntu is confused somehow.  The chipset is supported I know that much.

---

### Post by imhotep531 on 2011-07-27
Incidentally I thought about RMAing the card and ordering one that doesn't have any RAID capability just to be on the safe side.  But there really aren't any like that so hopefully I can make this work.

---

### Post by coffee412 on 2011-07-27
Hi, I have to leave for a service call pretty quick but wanted to ask this:

Is there a chance that you can run the drives off an existing motherboard sata port/s.?

Kinda bypassing the controller card. Just take the controller card out. BTW -- what controller card do you have?

Thanks,

coffee

---

### Post by imhotep531 on 2011-07-28
RAID controller card
[http://www.newegg.com/Product/Produc...82E16815124027](http://www.newegg.com/Product/Produc...82E16815124027)

Call me paranoid but I went ahead and reinstalled.  Before the first installation I had poked around with a live CD and attempted to do some partitioning with GParted and tried to figure out how to format and/or setup RAID with Disk Utility.  I had no idea what I was doing and I wanted some peace of mind that nothing I'd done was still messing me up with the full installation.

So we've got a clean slate.  Is this the right order to do things?

1. Remove any existing partitions one both drives with fdisk
2. Create one new partition on each drive with fdisk
3. Set partition type ID to 'fd' on each drive with fdisk
4. Create RAID 1 using both disks with mdadm
5. Create mdadm.conf
6. Format the new RAID 1 array
7. Mount the formatted RAID 1 array

I did notice something strange during the reinstallation.  It told me that RAID was detected and asked if I wanted to activate those devices.  This is strange because, first of all, the only disk that was detected during installation was the 80GB that's connected to the motherboard.  The add-on card and it's two 500GB disks were not detected (as far as I can tell).  BUT...the 80GB drive that was detected had 'SATA RAID' in its name.  This is also strange because my motherboard does not have any RAID capability so I don't know why the Ubunut installer is calling it a RAID device and asking me if I want to activate it?

Either the single 80GB is the RAID device that was detected, or my add-on card is it even though the installer did not list either of the drives connected to it.  This is really confusing!

---

### Post by SeijiSensei on 2011-07-28
coffee gave you the critical help.  The steps you list should give you the result you seek.

You should see whether you can disable any RAID features on your disk controller.  If so, turn them off.  Sometimes you can hit a key combination during boot to enter the controller's BIOS.  You don't want the controller interfering between the OS and the drives.

---

### Post by imhotep531 on 2011-07-28
> **SeijiSensei said:**
> coffee gave you the critical help.  The steps you list should give you the result you seek.

You should see whether you can disable any RAID features on your disk controller.  If so, turn them off.  Sometimes you can hit a key combination during boot to enter the controller's BIOS.  You don't want the controller interfering between the OS and the drives.

Yes we took care of this awhile ago.

---

### Post by imhotep531 on 2011-07-28
Coffee, I need to take a slight detour and then come back to this in a bit.  I'd like to setup ssh and dyndns so I can remote into the server from another computer.  This way I can at least have more flexibility with copying and pasting what I'm getting back in the terminal.

---

### Post by imhotep531 on 2011-07-29
Ok I'm back in the saddle.  After a fresh reinstallation of Ubuntu Server 10.04.2 LTS I have done nothing to this machine except configure ssh and ddclient, both of which are working flawlessly.

Here is the first output of fdisk -l

root@datahaus:/home/imhotep531# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e7a86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006874

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006874

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/md0: 500.1 GB, 500107771904 bytes
2 heads, 4 sectors/track, 122096624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006874

    Device Boot      Start         End      Blocks   Id  System

I have no idea where md0 came from.  Again this is right after reinstalling.  I have not set this drive up after reinstalling and my attempts to create md0 on the first installation were always unsuccessful.

According to fdisk /dev/md0 has no partitions defined yet.  If I want /dev/md0 to be used only for storage of lots of data (photos, music, documents, etc) should I create an extended or primary partition?

If I want /dev/md0 to be accessible by Windows machines so they can save and retrieve files from it, should I format it to NTFS or does it matter?

Thanks for sticking with me!

---

### Post by imhotep531 on 2011-08-01
Here's the detail on /dev/md0.  What I still don't get though is how this says it was created on July 20.  That predates my re-install of Ubuntu!  How is it still there?

root@datahaus:/home/imhotep531# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jul 20 20:24:47 2011
     Raid Level : raid1
     Array Size : 488386496 (465.76 GiB 500.11 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jul 20 22:35:13 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 68b931db:e547651e:992e1967:71e31acb (local to host datahaus)
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc

---

### Post by coffee412 on 2011-08-01
Well, See if you can format it.

> mkfs.ext3 /dev/md0

Update Time : Wed Jul 20 22:35:13 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

Raid looks to be in good shape too!

Make sure you have a working /etc/mdadm.conf file that is correct.

---

### Post by imhotep531 on 2011-08-02
I guess I am cursed.  So I used mkntfs to format /dev/md0 and now I'm getting this:

root@datahaus:/home/imhotep531# mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory

...and this....

root@datahaus:/home/imhotep531# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e7a86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/md_d0: 500.1 GB, 500107771904 bytes
2 heads, 4 sectors/track, 122096624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

      Device Boot      Start         End      Blocks   Id  System
/dev/md_d0p1   ?      822447   240553456   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/md_d0p2   ?   244156454   471478443   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/md_d0p3   ?    28216909    28216910           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/md_d0p4       330301441   330307927       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Nothing I've done so far seems like a normal series of events with Linux.  I want to use it but the amount of time it is wasting is insane.

---

### Post by imhotep531 on 2011-08-02
Now I'm really screwed.  I can't even stop or remove /dev/md0 to start over.  After formatting it now the system cannot do anything with it, including start over.

root@datahaus:/home/imhotep531# mdadm --stop /dev/md0
mdadm: error opening /dev/md0: No such file or directory

root@datahaus:/home/imhotep531# fdisk /dev/md0
Unable to open /dev/md0

---

### Post by imhotep531 on 2011-08-02
More info...

root@datahaus:/home/imhotep531# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md_d0 : active raid1 sdb[0] sdc[1]
      488386496 blocks [2/2] [UU]

unused devices: <none>


So is /dev/md0 gone and replaced by /dev/md_d0?  Apparently so...

root@datahaus:/home/imhotep531# mdadm --detail /dev/md_d0
/dev/md_d0:
        Version : 00.90
  Creation Time : Mon Aug  1 09:58:12 2011
     Raid Level : raid1
     Array Size : 488386496 (465.76 GiB 500.11 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Aug  1 20:25:05 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : b187a8f1:acac9825:992e1967:71e31acb (local to host datahaus)
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc

---

### Post by coffee412 on 2011-08-02
> Nothing I've done so far seems like a normal series of events with  Linux.  I want to use it but the amount of time it is wasting is insane. 	

You do seem to be having some problems here eh? 

Would you be up for a remote ssh session? I sure am curious about what is going on with your system. But there is always the security with an unknown user (grin).  Other than that all I can suggest is to basically start over and repartition the drives in the raid and see if things clear up.

Never had a problem with mdadm really working with drives. Should be a simple process.

coffee

---

### Post by coffee412 on 2011-08-02
md_d0

That expains why you cannot access md0 eh? Try this:

mkfs.ext3 /dev/md_d0

see if you format it.

---

### Post by imhotep531 on 2011-08-02
Making some progress...

Got rid of all partitions on /dev/sdb and /dev/sdc (the two disks I want to RAID 1)

Then discovered some partitions on the existing RAID 1 volume and got rid of those too before stopping that volume.

I THINK I'm back to a clean slate at this point.  So I then partitioned /dev/sdb and /dev/sdc, now I have /dev/sdb1 and /dev/sdc1.

I formatted both partitions as ext4.

[COLOR=Red]root@datahaus:/home/imhotep531# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e7a86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      191412   488385560   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      191412   488385560   83  Linux
[/COLOR]
[COLOR=Black]So next I did this:

[COLOR=Red]root@datahaus:/home/imhotep531# mdadm --create /dev/md0 -l 1 -n 2 /dev/sdb1 /dev/sdc1
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=488385560K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=488385560K  mtime=Wed Dec 31 19:00:00 1969
Continue creating array? y
mdadm: array /dev/md0 started.

[COLOR=Black]Yay, it says the array is started, but I'm not sure what to make of that bit about both partitions containing an ext2 file system since I just got done formatting them ext4.

Right now the new array is at 3% in the resyncing process....

[COLOR=Red]root@datahaus:/home/imhotep531# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Aug  2 10:10:51 2011
     Raid Level : raid1
     Array Size : 488385472 (465.76 GiB 500.11 GB)
  Used Dev Size : 488385472 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Aug  2 10:10:51 2011
          State : clean, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 3% complete

           UUID : e8fd13b5:0513b468:992e1967:71e31acb (local to host datahaus)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
[/COLOR]
[/COLOR][/COLOR]
[/COLOR]

---

### Post by coffee412 on 2011-08-02
Ok!!!!!!!!!

Your there. Now its just got to quit syncing and it will be ready. Dont worry about the ext2 discovery. Now after its all done remember to create a new /etc/mdadm.conf file like this:

> mdadm --detail --scan --verbose > /etc/mdadm.confThen your ready for action!!:P

Some helpful stuff here:

To remove a failed drive from the array:

> mdadm /dev/md0 -r /dev/sda1To add a drive to the array:

> mdadm /dev/md0 -a /dev/sda1
Enjoy the raid :guitar:
Oh, Make sure to mark your thread as solved.

coffee

---

### Post by imhotep531 on 2011-08-02
Done, here is the contents of mdadm.conf shown in vim

[COLOR=Red]ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=e8fd13b5:0513b468:992e1967:71e31acb
   devices=/dev/sdb1,/dev/sdc1[/COLOR]

[COLOR=Black]Do I need to mount the array or is it literally ready as-is?[/COLOR]

---

### Post by coffee412 on 2011-08-02
You will have to mount it and also add it to your /etc/fstab for it to automatically mount on reboots. So, Do the add to /etc/fstab first.

1. Edit your /etc/fstab and add the following line:

> /dev/md0   /mymountpoint   ext3   defaults   0 0Change the device and mountpoint to match your system.

Now mount it:
In a term window:

> sudo mount /dev/md0 /mymountpoint
Have fun!

---

### Post by imhotep531 on 2011-08-03
Remember yesterday when I created /dev/md0 and it told me that it was successfully started?  Well I guess it renames that raid array after syncing is complete because I get the following now:

[COLOR=Red]root@datahaus:/# mount /dev/md0 /nas
mount: special device /dev/md0 does not exist[/COLOR]

So I checked this....
[COLOR=Red]
root@datahaus:/# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e7a86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      191412   488385560   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      191412   488385560   83  Linux

Disk /dev/md_d0: 500.1 GB, 500106723328 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

      Device Boot      Start         End      Blocks   Id  System
/dev/md_d0p1               1      191412   488385560   83  Linux
[/COLOR]
Before I go any further I want to understand what is what.  [COLOR=Black]Do I mount /dev/md_d0 or do I mount /dev/md_d0p1?  What is the difference?

According to mdadm there is no difference:

[COLOR=Red]root@datahaus:/# mdadm --detail /dev/md_d0
/dev/md_d0:
        Version : 00.90
  Creation Time : Tue Aug  2 10:10:51 2011
     Raid Level : raid1
     Array Size : 488385472 (465.76 GiB 500.11 GB)
  Used Dev Size : 488385472 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Aug  2 20:33:33 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : e8fd13b5:0513b468:992e1967:71e31acb (local to host datahaus)
         Events : 0.38

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc[/COLOR]

AND[COLOR=Red]

root@datahaus:/# mdadm --detail /dev/md_d0p1
/dev/md_d0p1:
        Version : 00.90
  Creation Time : Tue Aug  2 10:10:51 2011
     Raid Level : raid1
     Array Size : 488384448 (465.76 GiB 500.11 GB)
  Used Dev Size : 488385472 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug  3 09:13:45 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : e8fd13b5:0513b468:992e1967:71e31acb (local to host datahaus)
         Events : 0.38

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc


[/COLOR] [/COLOR]

---

### Post by coffee412 on 2011-08-03
I would mount /dev/[COLOR=Black]/md_d0 and make sure your /etc/mdadm.conf file reflects it correctly. Then reboot system to make sure it comes back as an active device.


[/COLOR]> Well, here's the next chapter in this saga...
[COLOR=Black]
Kinda like Star Wars here! :)
[/COLOR]

---

### Post by imhotep531 on 2011-08-03
A long time ago in a server far far away...

Ok I have edited mdadm.conf to say this:

[COLOR=Red]ARRAY /dev/md_d0 level=raid1 num-devices=2 metadata=00.90 UUID=e8fd13b5:0513b468:992e1967:71e31acb
   devices=/dev/sdb1,/dev/sdc1[/COLOR]

I have a few questions:

1. Each disk seems to have two names in the output of fdisk -l.  For example, /dev/sdb is also called /dev/sdb1 and /dev/md_d0 is also called /dev/md_d0p1.  Which of these names should I put in mdadm.conf?  For now I have put the first one that leaves out the 'p1', but I wonder because in mdadm.conf it lists the two disks with the '1'.

2. On my server mdadm.conf is located in /home/imhotep531 instead of /etc.  Should I move it or leave as-is?  Is this perhaps due to a different version of mdadm or Ubuntu?

---

### Post by imhotep531 on 2011-08-03
I'm skipping ahead...

So I just got this:

[COLOR=Red]root@datahaus:/home/imhotep531# mount /dev/md_d0 /nas
Failed to read last sector (976772991): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/md_d0': Invalid argument
The device '/dev/md_d0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]

Since it suggests trying to mount a partition instead of the whole disk, I tried using this:

[COLOR=Red]root@datahaus:/home/imhotep531# mount /dev/md_d0p1 /nas
mount: wrong fs type, bad option, bad superblock on /dev/md_d0p1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR]

Ideas?

---

### Post by coffee412 on 2011-08-03
Did you edit your fstab file like I mentioned a few posts ago and add the line with the right devices? Ok, The line in your fstab file should read:

> /dev/md_0     /nas     ext3   defaults   0 0

I dont like ntfs partitions they get messy. Make sure you formatted the device using the following command.

sudo mkfs.ext3 /dev/md_0

ext3 file system is just fine for doing most things. Use it. YOu can share it out to windows boxes later with samba if you want. 

1. Make sure /nas is actually there
2. Make sure you have your /etc/fstab file setup correctly
3. Make sure you formatted the array (/dev/md_0) correctly

With your fstab setup correctly you just issue a basic mount command for the drive as it will pull the info from your fstab as far as format type and such.

> mount /dev/md_0


Experience is the best teacher.

coffee

---

### Post by nipennem on 2011-08-03
> **imhotep531 said:**
> 
3. Set partition type ID to 'fd' on each drive with fdisk

Just a few notes, hope they clarify things

[LIST=1]
[*]**mdadm does not care about partition types.** If you give it a partition as RAID device, it won't consider the rest of the disk and that includes the partition table.

The partition table is read by the kernel to create /dev/sdXN (X = a, b, ...; N = 1, 2, ...) devices. Similarly, the **partition type 0xfd is used by the kernel** for RAID autodetection -- a feature which is now **deprecated**.

[*]Setting the partition type to 0x83 is not the best choice, because 0x83 indicates the partition is a 'Linux Data' partition which typically contains a mountable filesystem. A good type may be 0xDA ("non-filesystem data").

[*]It is totally pointless and masochistic to use a non-Linux operating system for which you have to rely on FUSE such as NTFS on a Linux software RAID array. You will never be able to access the array outside Linux anyway, so you might just as well pick one that is fully supported by the Linux kernel. This will improve the 'filesystem performance' drastically.

[/LIST]

---

### Post by coffee412 on 2011-08-03
> **nipennem said:**
> Just a few notes, hope they clarify things

[LIST=1]
[*]**mdadm does not care about partition types.** If you give it a partition as RAID device, it won't consider the rest of the disk and that includes the partition table.

The partition table is read by the kernel to create /dev/sdXN (X = a, b, ...; N = 1, 2, ...) devices. Similarly, the **partition type 0xfd is used by the kernel** for RAID autodetection -- a feature which is now **deprecated**.
[*]Setting the partition type to 0x83 is not the best choice, because 0x83 indicates the partition is a 'Linux Data' partition which typically contains a mountable filesystem. A good type may be 0xDA ("non-filesystem data").
[*]It is totally pointless and masochistic to use a non-Linux operating system for which you have to rely on FUSE such as NTFS on a Linux software RAID array. You will never be able to access the array outside Linux anyway, so you might just as well pick one that is fully supported by the Linux kernel. This will improve the 'filesystem performance' drastically.
[/LIST]


Thank you for your input. For me it was hard learning about raid when I did because all the info on it was rather dated. Nice to see someone chime in that can add some meat to the problem. Now, Where were you about 10 posts ago!!! :)

A little about myself, I dont use anything microsoft and dont care too. Infact, I got so pushed off by MS that when I couldnt find a good all round Newgroup posting program I wrote one in bash using zenity menus! :P I hate MS crap.

> You will never be able to access the array outside Linux anywayI guess I dont follow you here ^. Of course you can. Just share it out. 

One thing in mind here. This is his first RAID indever and its best to Keep it simple (KISS) and just get it up and running. Of course the icing on the cake is adjusting for all the little niceities that will give you a performance boost. However, For a first time learning its best to create a standard no frills raid.

Im very proud of imhotep531 for sticking it out and not giving up. Now he has learned quite a bit and eventually help others.

Have a great day and thanks for your posting.

coffee

---

### Post by imhotep531 on 2011-08-03
First in answer to your question, yes previously I edited fstab to look like this (the last line is what I added):

[COLOR=Red]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nvidia_afgceafe1 /               ext4    errors=remount-ro 0       1
/dev/mapper/nvidia_afgceafe5 none            swap    sw              0       0
/dev/md0 /nas ext4 defaults 0 0[/COLOR]

Now I have changed the last line to read:
[COLOR=Red]/dev/md_d0 /nas ext4 defaults 0 0[/COLOR]

And then remounted:

[COLOR=Red]root@datahaus:/home/imhotep531# mount /dev/md_d0 /nas
Failed to read last sector (976772991): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/md_d0': Invalid argument
The device '/dev/md_d0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]

So next I tried this as the last line in fstab:
[COLOR=Red]/dev/md_d0p1 /nas ext4 defaults 0 0[/COLOR]

And then remounted:

[COLOR=Red]root@datahaus:/home/imhotep531# mount /dev/md_d0p1 /nas
mount: wrong fs type, bad option, bad superblock on /dev/md_d0p1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/COLOR]

Next I ran dmesg | tail as the output suggests and got this:

[COLOR=Red]root@datahaus:/home/imhotep531# dmesg | tail
[   12.563150] md: bind<sdb>
[   12.573412] md: bind<sdc>
[   12.776120] raid1: raid set md_d0 active with 2 out of 2 mirrors
[   12.776145] md_d0: detected capacity change from 0 to 500106723328
[   12.776378]  md_d0: p1
[   12.777301] md_d0: p1 size 976771120 exceeds device capacity, limited to end of disk
[   22.390006] eth0: no IPv6 routers present
[ 3297.576133] ip_tables: (C) 2000-2006 Netfilter Core Team
[15511.796324] EXT4-fs (md_d0p1): bad geometry: block count 122096390 exceeds size of device (122096112 blocks)
[22692.195425] EXT4-fs (md_d0p1): bad geometry: block count 122096390 exceeds size of device (122096112 blocks)[/COLOR]

---

### Post by imhotep531 on 2011-08-03
> **coffee412 said:**
> 
1. Make sure /nas is actually there
2. Make sure you have your /etc/fstab file setup correctly
3. Make sure you formatted the array (/dev/md_0) correctly


1. I checked for /nas after creating it and its there.
2. I"m not sure if I do or not.  I'm still confused on theh whole /dev/md_d0 vs /dev/md_d0p1 thing.

and now for a whopper...

3. Here's the thing, I did run mkntfs on it initially.  That was a mistake.  So I deleted the partitions formatted as NTFS and created new ones, and formatted with ext4 instead.  I have a theory that I'd like your opinion on.  I keep seeing 'ghosts' on these drives in the form of error messages that list things I thought I had overwritten.  For example, the error that mentions NTFS when I deleted those partitions and reformatted to ext4.  Another 'ghost' is how Ubuntu lists Sil and nVidia RAID on my 80GB drive which is NOT connected to any RAID capable ports on the motherboard.  I finally remembered that in a former life this same hard drive was in a RAID 1 array on an ASUS motherboard that did have nVidia and Sil chipsets.

So somehow these drives are NOT getting fully erased when I partition and format them.  The headers (or whatever you call the sections where RAID info is stored) have not been cleared despite all the formatting and partitioning I've been doing.

After everything I've learned I would feel comfortable doing it all over again, so here is the million dollar question....  is there a BETTER or more complete way to TOTALLY erase all the crap on a hard drive other than what I've been doing?  If so I want to do this because I keep seeing these errors listing things that shouldn't even be in the equation at this point.

---

### Post by coffee412 on 2011-08-03
> After everything I've learned I would feel comfortable doing it all over  again, so here is the million dollar question....  is there a BETTER or  more complete way to TOTALLY erase all the crap on a hard drive other  than what I've been doing?  If so I want to do this because I keep  seeing these errors listing things that shouldn't even be in the  equation at this point.In all my years I have not ever heard of a drive that would not totally erase if you removed the partition(s). I have seen instances where people have made mistakes in fdisk that lead to this problem. Therefore, Lets just wipe and reload.

In fdisk make sure you remove all partitions and write changes to disk on the disks.

Now we will FORCE the re-reading of the partition tables:

> partprobe /dev/sdb
partprobe /dev/sdcNow go into fdisk and setup 1 partition on each drive. I would still set the partition type as fd. Then write changes to disks. Partprobe the drives again.

Now get rid of your /etc/mdadm.conf file

> rm -f /etc/mdadm.conf
Now recreate your raid device:

> mdadm --create /dev/md0 --level=raid1 --force /dev/hdb1 /dev/hdc1
Now if we get that far we can format it:

> mkfs.ext3 /dev/md0Make a mount point for the raid:

> mkdir /mnt/raid1Edit the fstab file and add your entry for the raid.

> /dev/md0   /mnt/raid1 ext3   defaults   0 0
Then finally mount the darn thing

> mount /dev/md0?

---

### Post by imhotep531 on 2011-08-06
Ok coffee, I think we are closer than ever to licking this thing.  I couldn't live with the fact that Ubuntu is still detecting RAID information on these disks from years ago when they were part of a Windows system.  So I blitzed them all with shred, reinstalled Ubuntu Server 10.04.2 LTS and was very happy to discover no more weird RAID arrays being detected, neither during installation nor when I ran dmraid -r.  Finally that mystery is solved.

Next I quickly went through these steps:

partprobe /dev/sdb
partprobe /dev/sdc      
                           
Now go into fdisk and setup 1 partition on each drive. I would  still set the partition type as fd. Then write changes to disks.  Partprobe the drives again.

Now get rid of your /etc/mdadm.conf file

     Quote:
                                                 rm -f /etc/mdadm.conf                                 
Now recreate your raid device:

     Quote:
                                                 mdadm --create /dev/md0 --level=raid1 --force /dev/hdb1 /dev/hdc1                                 
Now if we get that far we can format it:

     Quote:
                                                 mkfs.ext3 /dev/md0                                 
Make a mount point for the raid:

     Quote:
                                                 mkdir /mnt/raid1                      

Now for the next obstacle which is hopefully a minor one.  When I run fdisk -l it says that /dev/md0 has no valid partition table

[COLOR=Red]root@datahaus:/# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f7a27fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      191412   488385560   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82b02862

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      191412   488385560   fd  Linux raid autodetect

Disk /dev/md0: 500.1 GB, 500106723328 bytes
2 heads, 4 sectors/track, 122096368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table[/COLOR]

I thought if both disks participating in the RAID were partitioned and formatted before creating the array then it would be fine, so should I worry about this?

---

### Post by coffee412 on 2011-08-06
Hi, I wouldnt worry about it. You want to format the the raid after its created not before. Just try and create your array (raid) now and see what happens.

Me? Well, I have been fooling around with virtualbox. You see, Bought an upgrade. I have the AMD T1099 6 core running on my system with 8 gigs ram now. So, Its just a forgone conclusion that I try out virtualbox. Now I have Ubuntu 10.04 running on my Fedora 14 !

Anyways, Back to your raid. I would just go about assembling it and see how it goes... 

Let me know....

coffee

---

### Post by imhotep531 on 2011-08-08
Sorry to be so thick, but I don't understand the sequence of events you listed earlier.  It said to partition and format each of the disks that would participate in the raid BEFORE creating the raid.  So why did I need to do that if I have to partition and format the raid array AFTER it is created anyway?

Today I restarted the server and now its telling me that /dev/md0 does not exist when I just created it yesterday.

Also, when I try to add /dev/sdb and /dev/sdc into a new array, it tells me they appear to already be a part of one.

!!!!

Either its there or it isn't.  I just do not understand how Ubuntu software raid works I guess.  The outputs constantly contradict each other and I never know what the heck is going on.  Very frustrating but I'm willing to stick it out a little while longer.

---

### Post by coffee412 on 2011-08-08
In a normal setup of a drive you would partition the drive and then format it. Then its ready to use. However, When working with raids you would partition the drive, Then setup the raid thru mdadm and THEN format the raid (not the individual drives). 

fsck.ext3 /dev/md0

Then its ready for use. You then mount it and go.

better??

---

### Post by imhotep531 on 2011-08-08
Ok thanks coffee I appreciate the clarification.  I also read through this guide and it helped me understand the whole process more clearly.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

Right now I'm waiting on the array to finish resyncing and then I'll format it.

I still don't get why it told me that /dev/md0 did not contain a valid partition table yesterday when I tried to format it.

---

### Post by imhotep531 on 2011-08-08
Ha!  Look at the responses to the same question in this thread:

[http://www.webhostingtalk.com/showthread.php?t=1025964](http://www.webhostingtalk.com/showthread.php?t=1025964)

Knowing is half the battle, as they say.  So now I know I can ignore that error and format the array anyway.

---

### Post by coffee412 on 2011-08-08
> **imhotep531 said:**
> Ha!  Look at the responses to the same question in this thread:

[http://www.webhostingtalk.com/showthread.php?t=1025964](http://www.webhostingtalk.com/showthread.php?t=1025964)

Knowing is half the battle, as they say.  So now I know I can ignore that error and format the array anyway.

Well, I dont follow those posts at all. /dev/md0 has nothing to do with LVM (logical Volume Management) they are two seperate beasts. 

Raids do contain file systems. Otherwise we would not use them. Of course the proof is in the pudding. After your done formating your raid do an ls on it and there is your file system!

I guess they didnt know what they are talking about and you qouted it as funny?

---

### Post by imhotep531 on 2011-08-08
No I wasn't kidding I was just pointing out that this error I keep getting seems to be erroneous.  I'm referring to the error about /dev/md0 not containing a valid partition table.  I keep getting this error and I'm following the steps to the letter.  My experience up to this point is that you can't get around this error no matter what so I guess I'm a believer until somebody proves me wrong.

This time around I created new partitions on each disk (/dev/sdb and /dev/sdc) but I did not format them.  Then I created /dev/md0.

Here are the results of cat /proc/mdstat

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[1] sdb1[0]
      488385472 blocks [2/2] [UU]

unused devices: <none>

```

So far so good.

Next I formatted /dev/md0 with mkfs.ext4, created a new mdadm.conf file, created a mount point, edited /etc/fstab, and finally mounted the array.

Here are the results of df -k

```
root@datahaus:/# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73744616   1276980  68721588   2% /
none                   1958628       248   1958380   1% /dev
none                   1963192         0   1963192   0% /dev/shm
none                   1963192       284   1962908   1% /var/run
none                   1963192         0   1963192   0% /var/lock
none                   1963192         0   1963192   0% /lib/init/rw
none                  73744616   1276980  68721588   2% /var/lib/ureadahead/debugfs
/dev/md0             480720528    202664 456098592   1% /nas

```

So I guess that's it....knock on wood.  I'm almost afraid to restart the server for fear my array won't come back up.  This has been WAY more effort than it needed to be but I'll chalk it up to being a newbie.  Thanks for sticking with me coffee!!!

---

### Post by coffee412 on 2011-08-08
> This has been WAY more effort than it needed to be but I'll chalk it up  to being a newbie.  Thanks for sticking with me coffee!!!

When I was just learning linux (many moons ago) we had to compile our own kernel and then setup our Xorg.conf file and compile a driver for our video card. It took me weeks to get it right. Be glad those days are gone!

Im proud that you stuck to it and got it done. Yes, Its hard at first but people like you that have that stick-to-it-nuss will go far!

Congradulations on your accomplishment!! 

Now lets delete the raid and do it again! :P:P:P:P

Just joking!

coffee

---

### Post by imhotep531 on 2011-08-08
Well I may have spoke too soon :(

When I restarted the system I got this output before it would let me login:
```

The disk drive for /nas is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery
```

I pressed S to skip.  Here are some outputs I've dug up after the first reboot, maybe there's a clue in here somewhere:

cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc[1] sdb[0]
      488385472 blocks [2/2] [UU]

unused devices: <none>
```

Ok so the array is active.

df -k
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73744616   1278632  68719936   2% /
none                   1958628       224   1958404   1% /dev
none                   1963192         0   1963192   0% /dev/shm
none                   1963192       292   1962900   1% /var/run
none                   1963192         0   1963192   0% /var/lock
none                   1963192         0   1963192   0% /lib/init/rw
```

So it does not appear to be mounted.  And finally...

vim /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b4b76f90-2a6c-4b89-a5e8-b015583f1138 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aac8d326-986a-4bbc-a68f-69c04af38b98 none            swap    sw              0       0
/dev/md0        /nas    ext4    defaults        1       2

```

If I try to remount it I get this:
```
root@datahaus:/home/imhotep531# mount /dev/md0 /nas
mount: you must specify the filesystem type
```

So to sum up, the array is still there but there's a problem with the mount point of /nas at reboot.  Did I make a mistake with the fstab file?

---

### Post by imhotep531 on 2011-08-08
I just noticed something....both of the partitions that participate in the array are gone!  Look at the output from fdisk -l I posted above.  /dev/sdb1 and /dev/sdc1 are gone after the first reboot following the successful creation of the array.

So how on earth can it still be active in the output of cat /proc/mdstat ??!!

---

### Post by coffee412 on 2011-08-08
Check your fstab and change the 1 and 2 to both 0

---

### Post by Habitual on 2011-08-08
> **coffee412 said:**
> When I was just learning linux (many moons ago) we had to compile our own kernel and then setup our Xorg.conf file and compile a driver for our video card. It took me weeks to get it right. Be glad those days are gone!

I was there too (circa mid to late '90s).
I for one am glad the Dark Ages of Linux Computing are over. :)

---

### Post by imhotep531 on 2011-08-09
Ok, started fresh and this time edited /etc/fstab as coffee directed, with 0 0 instead of 1 2 as the tutorial directed.

Output of cat /proc/mdstat
```
Personalities : [raid1]
md0 : active raid1 sdc1[1] sdb1[0]
      488385472 blocks [2/2] [UU]

unused devices: <none>
```

Output of fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036374

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc8fc026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      191412   488385560   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0515eb19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      191412   488385560   fd  Linux raid autodetect

Disk /dev/md0: 500.1 GB, 500106723328 bytes
2 heads, 4 sectors/track, 122096368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

There's that pesky message again, saying my new array doesn't have a valid partition table.  I'm going to ignore.

Output of df -k showing the mounted array
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73744616   1278316  68720252   2% /
none                   1958756       248   1958508   1% /dev
none                   1963192         0   1963192   0% /dev/shm
none                   1963192       292   1962900   1% /var/run
none                   1963192         0   1963192   0% /var/lock
none                   1963192         0   1963192   0% /lib/init/rw
none                  73744616   1278316  68720252   2% /var/lib/ureadahead/debugfs
/dev/md0             480720528    202664 456098592   1% /home/nas
```

I'm doing all of this via SSH so I won't restart yet to check if the array mounts on reboot.  I'll do that a bit later when I'm in front of the machine so I can skip past the error if necessary.

Here's hoping it works!  Good giref, if it doesn't then I'm throwing in the towel.  I'll setup fakeRAID before I spend another three weeks trying to setup something as basic as  RAID 1.  This took minutes on my previous Windows machine (gasp).

---

### Post by coffee412 on 2011-08-09
Things so far look fine to me. I would not be concerned about the "valid partition" problem. However, I would make one minor change that really will not effect anything.

I would change your mount point to the /mnt directory. Thats what the mount directory is for. Its not a "gotta do thing" but its just good practice.

If your going to allow others to store on it via ssh or webdav then you can just create a link in their home directory to it.

Otherwise, Looks good to go and I would start using it.

coffee:D

---

### Post by imhotep531 on 2011-08-09
Ok I remounted /dev/md0 to /mnt/nas.  After triple checking everything I rebooted the system and got this before it would give me a login prompt:

```
fsck from util-linux-ng 2.17.2
mount: wrong fs type, bad option, bad superblock on /dev/md0,
missing codepage or helper program, or other error
In some cases useful info is foundin syslog - try
dmesg tail or so

mountall: mount /home/nas [703] terminated with status 32
mountall: Filesystem could not be mounted: /home/nas
An error occurred while mounting /home/nas
Press S to skip mounting or M for manual recovery
```Every seen this before?

I don't know what to say, I guess I'm starting to lose my will to keep messing with it.  I feel like we left ridiculous a long way back ;)  I have followed the Ubuntu guide to the letter and cross-referenced with your advice as well as online tutorials.  Basically I cannot reproduce anything resembling a functional array that doesn't evaporate after a simple reboot.

So anyhow, I hit S to skip that error and started digging around.  Check this out....

```
Disk /dev/md0: 500.1 GB, 500106723328 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0515eb19

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      191412   488385560   fd  Linux raid autodetect
```

I DID NOT create /dev/md0p1.  I never partitioned the array.  I mean good grief, if Ubuntu is just going to create partitions for me whenever it sees fit...

I'm just thinking out loud here -- maybe it needs this partition so I'll go with it and see what happens.  I'll mount /dev/md0p1.

```
root@datahaus:/home/imhotep531# mount /dev/md0p1 /home/nas
mount: wrong fs type, bad option, bad superblock on /dev/md0p1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Nope, it just give me the same error I saw after rebooting.

Sigh...

---

### Post by imhotep531 on 2011-08-09
My last ditch effort to make sense of it:

I figured I'd treat this mysterious /dev/md0p1 like any other partition and format it.  So I formatted it to ext4.  This appeared to be successful.

Next I tried to mount it:

```
root@datahaus:/home/imhotep531# mount /dev/mp0p1 /mnt/nas
mount: special device /dev/mp0p1 does not exist
```

What?!?!?

---

### Post by coffee412 on 2011-08-09
> **imhotep531 said:**
> My last ditch effort to make sense of it:

I figured I'd treat this mysterious /dev/md0p1 like any other partition and format it.  So I formatted it to ext4.  This appeared to be successful.

Next I tried to mount it:

```
root@datahaus:/home/imhotep531# mount /dev/mp0p1 /mnt/nas
mount: special device /dev/mp0p1 does not exist
```What?!?!?

Thought your raid was /dev/md0 ????

Ive had the no mount problem before. I do believe I put a line in /etc/rc.d/rc.local at the end to mount it there. No biggy:

but you should be mounting /dev/md0. That is your raid. Forget about the other.

---

### Post by imhotep531 on 2011-08-10
coffee, I guess I'm not making sense or not typing enough to describe what's going on.  To reiterate, I did mount /dev/md0 to /mnt/nas (scroll up to read my earlier post).  Mounting /dev/md0 was the last thing I did before I rebooted the system.

When the system rebooted it gave me the error about /mnt/nas not being ready.

---

### Post by coffee412 on 2011-08-10
> **imhotep531 said:**
> coffee, I guess I'm not making sense or not typing enough to describe what's going on.  To reiterate, I did mount /dev/md0 to /mnt/nas (scroll up to read my earlier post).  Mounting /dev/md0 was the last thing I did before I rebooted the system.

When the system rebooted it gave me the error about /mnt/nas not being ready.

Open a term window and try mounting it manually.

sudo mount /dev/md0

If that works then its a problem with the boot up sequence. The raid isnt ready in time for the mount command on bootup. Ive had that problem before. So I added a line to /etc/rc.d/rc.local (at the bottom) to mount it when I login.

mount /dev/md0

---

### Post by imhotep531 on 2011-08-10
> **coffee412 said:**
> Open a term window and try mounting it manually.

sudo mount /dev/md0

If that works then its a problem with the boot up sequence. The raid isnt ready in time for the mount command on bootup. Ive had that problem before. So I added a line to /etc/rc.d/rc.local (at the bottom) to mount it when I login.

mount /dev/md0

Yeah mounting it during a session works just fine.  It pukes after reboot.

Ok I'll try editing the file you suggested.  It makes sense, that is interesting.  So if I add that line at the bottom it tells Ubuntu to hold off mounting until after I login?  How long does it usually take to finish mounting an array?  Is it seconds or minutes?

coffee, I must say you are one of the most benevolent forum members I've ever met.  Thank you for sticking with me.

---

### Post by coffee412 on 2011-08-10
Hi,

You can add some stuff to make it delay after you login. Something like this:

> sleep 5
mount /dev/md0Basically means wait 5 seconds and then mount the raid.

> coffee, I must say you are one of the most benevolent forum members I've ever met.  Thank you for sticking with me.     
As long as one is willing to spend the time working on a problem I am glad to help. Its those that just give up I dont care for. After all, We must remember the ultimate quest --> To free us from the evil MS Windows! :D:D

---

