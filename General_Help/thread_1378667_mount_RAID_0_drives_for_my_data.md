---
title: "mount RAID 0 drives for my data"
date: 2010-01-11
forum: General Help
---

### Post by legolas on 2010-01-11
Hello all!   I just bought two 500gig hard disks to set up for RAID 0 for speedy read/write of data. I have read a lot of threads about putting Ubuntu on a RAID set, but I can't find anything about how to just mount the disks as a RAID set for use with my already existing 64 bit Karmic setup.
I am not to experienced with this sort of thing, so I was looking for a Howto, or a fairly detailed thread on this subject.  Can anyone point me in the right direction?
I know it is kind of a risky set-up, but I plan to back up regularly so I think I will be good.
Thank you so much- I can hardly wait to start striping!

---

### Post by legolas on 2010-01-12
Update:
I followed a tutorial in Ubuntu Help that said to use the alternate CD to set up the RAID drives and install.  I just did the first part to partition the 2 RAID drives and then exited the install because I don't need an install, I just need the drives set up.  Unfortunately after doing that, Ubuntu would not boot with the two RAID drives plugged in, but when I unplugged them from the system, my Ubuntu booted up fine.  Weird.  Still not getting anywhere by myself.  Help anyone?

---

### Post by wkulecz on 2010-01-12
Are you trying to use "fakeraid" where the disk are assigned to the raid array with your system BIOS, or mdadm "software raid"?

The proceedures are different, I can't help with fakeraid as IMHO the only reason to use it is to dual boot the array partitions with windows.

For software raid if you are not booting from the array, just boot normally and read up on mdadm.  You should be able to setup the disks and assemble the array from commands after an sudo -i terminal session.

I'm only using raid1 and raid5 on 6.06 and have concluded its more trouble than its worth (YMMV) so my knowledge is not current.

You are aware that raid0 will loose all the data on both drives if one fails, aren't you?  I've never found speed worth the risk of data loss (YMMV).

--wally.

---

### Post by legolas on 2010-01-12
I am using an Elitegroup P55H-A Motherboard. Is that fake RAID?
Which is faster?
Like I said, I know it is kind of a risky set-up if I were to loose a disk and all, but I plan to back up regularly so I think I will be good.
Also, why can't I boot with the soon-to-be RAID disks plugged in do we suppose?

---

### Post by legolas on 2010-01-13
Ok, I have dinked some more with it and have seem to make a little headway, but now am at another roadblock.
The Palimpsest Disk Utility shows both of my 500gig drives that I want to stripe.  It then shows them again as a )Kb Raid-0 drive and describes it as 
"Striped (RAID 0)"
"2 Components (500 GB each)"
"Not running, partially assembled."

Can anyone see a hole in this setup?
There is a ton of threads on how to put Ubuntu on a raid set, but not how to just add a raid set for data.

Here is some info on the setup so far.
Any help is much appreciated.
Thank you.





sudo fdisk -l
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006452b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063b92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4309    34612011   83  Linux
/dev/sdc2            4310        4500     1534207+   5  Extended
/dev/sdc5            4310        4500     1534176   82  Linux swap / Solaris

Disk /dev/sdd: 185.3 GB, 185283624960 bytes
255 heads, 63 sectors/track, 22526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c4f9c4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2474    19872373+   7  HPFS/NTFS
/dev/sdd3            5029       22526   140552685    5  Extended
/dev/sdd5            5029       22526   140552653+   b  W95 FAT32



cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sda1[0](S)
      488383936 blocks
       
unused devices: <none>



df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              33G  8.6G   23G  28% /
udev                  2.0G  324K  2.0G   1% /dev
none                  2.0G  904K  2.0G   1% /dev/shm
none                  2.0G  104K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sdd5             134G   85G   50G  64% /media/disk



sudo mdadm --query /dev/md_d0
 
/dev/md_d0: is an md device which is not active




sudo mdadm --assemble --scan
mdadm: /dev/md/0 assembled from 1 drive - not enough to start the array.
mdadm: No arrays found in config file or automatically

---

### Post by legolas on 2010-01-17
Well, I was hoping it was not going to take as long as it did, but after working on it all week long, I finally found out the problem.  It seems the tutorial I was following was incomplete in its instructions.  I ended up using two different tutorials and merging them into one, complete version.  The first tutorial which was good, but missing an important step is:
[http://www.beginlinux.com/server_training/server-managment-topics/999-raid-0-on-ubuntu-804](http://www.beginlinux.com/server_training/server-managment-topics/999-raid-0-on-ubuntu-804)

It was good but, for brevity I believe, the important step of making sure that your mdadm.conf is complete was left out.  What ended up happening was that my mdadm.conf was not being filled in completely so the drives my raid set should be assembled by was not written in.  Not an enormous problem but when I turned off the computer and signed in the next time, the raid set would not assemble by itself and was just "busy" not letting me do squat.  It took me most of the week just to find out that I needed the mdadm.conf to say what the raid drives names, example- DEVICE /dev/sda* /dev/sdb*
I found that in:
[http://wiki.xtronics.com/index.php/Raid#Creating_the_file_systems_and_Mount_them](http://wiki.xtronics.com/index.php/Raid#Creating_the_file_systems_and_Mount_them)

After I got that in the mdadm.conf, it ran like a champ!

I hope this helps someone out.

---

