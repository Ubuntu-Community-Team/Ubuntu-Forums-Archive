---
title: "Auto-Start software RAID at Boot-Time in 9.10"
date: 2009-11-17
forum: General Help
---

### Post by jamesisin on 2009-11-17
I have created a new array using the newly included Palimpsest partitioning software in Ubuntu 9.10.  However, this array is not loaded until I manually start it (by running Palimpsest and telling it to start it) after logging in.

Clearly this will not work for serving to other machines.

Can someone give me the code necessary to make 9.10 auto-start this RAID during boot?

I believe I understand well enough how to auto-mount a drive and will use this once I am able to auto-start the array:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

---

### Post by BrokenKingpin on 2009-11-17
You need to add the definition of your raid array to mdadm.conf for it to start on boot:

1. From the Terminal run the following command to open the config file:
  sudo gedit /etc/mdadm/mdadm.conf

2. At the bottom of the file add the raid definition. For example, a two disk raid 1 array would look like this (use  palimpsest to get device names):
  DEVICE /dev/sdb1 /dev/sdc1
  ARRAY /dev/md0 level=raid1 devices=/dev/sdb1,/dev/sdc1

This should start the raid array at boot. For more details check out the mdadm documentation on their website. 

Now all you need to do is add md0 to your fstab file to have it automatically mount at boot:

1. From the Terminal run the following command to open the config file:
  sudo gedit /etc/fstab

2. Add md0 mount definition to the bottom of the file. For example:
  /dev/md0  /media/data  ext4  user,nosuid,noexec,nodev  0  0

Hope this helps!

---

### Post by jamesisin on 2009-11-18
Ah, this looks perfect.  I won't be able to test it for a couple of days, but I will report back when I am able to do so.  Thanks.

---

### Post by linuxdoctor on 2009-12-01
I am having the same problem.  I can start the array manual but will not start at boot up.

Any ideas?

**mdadm.conf:**
DEVICE /dev/sdb /dev/sdc
ARRAY /dev/md0 level=raid0 devices=/dev/sdb1,/dev/sdc1


**fstab:**
/dev/md0 /media/Storage ext4 user,nosuid,noexec,nodev 0 0

**/proc/mdstat:** *(when the array is started)*
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdc1[0] sdb1[1]
      781417472 blocks super 1.2 64k chunks
      
unused devices: <none>

**fdisk -l:**
Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fb4c06a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       36483   244220130    5  Extended
/dev/sda5            6080        7295     9767488+  82  Linux swap / Solaris
/dev/sda6            7296       36483   234452578+  83  Linux

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3da6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9d88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/md0: 800.2 GB, 800171491328 bytes
2 heads, 4 sectors/track, 195354368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x0003d642

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1   195354368   781417470   83  Linux

---

### Post by kemere on 2009-12-08
In the DEVICE line, do you need /dev/sdb_1_ and /dev/sdc_1_?

> 
**mdadm.conf:**
DEVICE /dev/sdb /dev/sdc
ARRAY /dev/md0 level=raid0 devices=/dev/sdb1,/dev/sdc1

---

### Post by jamesisin on 2009-12-08
With the numeric specification is how BrokenKingpin wrote his suggestion.  I'd give that a shot.

I ended up scrapping the RAID1 idea and moving to a sync script (which I have yet to put together) for unrelated reasons.

My first inclination would be to attempt it with the numeric specification, then without (if that fails) and see what comes of it.

---

### Post by nederlander on 2009-12-10
Thanks, this helped a lot, works perfect !

---

### Post by jamesisin on 2009-12-10
Very cool.  Which version worked for you?

---

### Post by devnull on 2009-12-11
BrokenKingpin, your post was spot on for me and my Software Raid5 setup.  It auto starts and mounts the array on boot without a problem.  Thank you very much!

---

### Post by BrokenKingpin on 2009-12-12
I am glad I could help.

---

### Post by Rychard on 2010-01-03
Thanks guys for this ... solved my problem too.  Post at 2.09am (!) on 18 Nov was the key.  Using 9.10.

---

### Post by jamesisin on 2010-01-04
Great.  Looks like this is solving the problem as posted so I am going to mark this thread as such.

---

