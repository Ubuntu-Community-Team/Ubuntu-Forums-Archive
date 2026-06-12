---
title: "move existing software raid to existing ubuntu system"
date: 2009-06-26
forum: General Help
---

### Post by lewinb on 2009-06-26
I am running Jaunty on a Dell Poweredge 700 server. I'm attempting to move/add two storage drives in software RAID1 from a linux based nas to the server. I'm having some problems getting it set up, and would appreciate help!

I've attached the two drives to the two internal SATA ports, and they show up as sda and sdb in gparted.

gparted recognizes that the drives are formatted ext3. It recognizes that they are part of a raid and the partitions on them, but doesn't do anything else. 

according to this thread
[http://ubuntuforums.org/showthread.php?t=850229&highlight=possible+to+move+software+raid+from+one+computer+to+another%3F](http://ubuntuforums.org/showthread.php?t=850229&highlight=possible+to+move+software+raid+from+one+computer+to+another%3F)

I should simply be able to use
 sudo mdadm --assemble --scan


to get ubuntu to detect the raid. But mdadm doesn't find them. 

Here's what's happening:
```
Poweredge:~$ sudo mdadm --assemble --scan
mdadm: No arrays found in config file or automatically


lewinb@Poweredge:~$ sudo mdadm --query /dev/sda2
/dev/sda2: is not an md array
/dev/sda2: device 1 in 2 device undetected raid1 /dev/md0.  Use mdadm --examine for more detail.
lewinb@Poweredge:~$ sudo mdadm --query /dev/sdb2
/dev/sdb2: is not an md array
/dev/sdb2: device 0 in 2 device undetected raid1 /dev/md0.  Use mdadm --examine for more detail.
```

Huh??? Is mdadm saying it recognizes it as a raid or not?? I don't understand The output from dmadm because it seems contradictory.

```
lewinb@Poweredge:~$ sudo mdadm --examine /dev/sda2
/dev/sda2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ef6853e4:06b78687:9aa924e0:4d08f2c8
  Creation Time : Thu Aug 28 02:53:54 2008
     Raid Level : raid1
  Used Dev Size : 975249856 (930.07 GiB 998.66 GB)
     Array Size : 975249856 (930.07 GiB 998.66 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Jun 27 10:06:20 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5434f888 - correct
         Events : 852736


      Number   Major   Minor   RaidDevice State
this     1       8       18        1      active sync   /dev/sdb2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2
lewinb@Poweredge:~$ sudo mdadm --examine /dev/sdb2
/dev/sdb2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : ef6853e4:06b78687:9aa924e0:4d08f2c8
  Creation Time : Thu Aug 28 02:53:54 2008
     Raid Level : raid1
  Used Dev Size : 975249856 (930.07 GiB 998.66 GB)
     Array Size : 975249856 (930.07 GiB 998.66 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Jun 27 10:06:20 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5434f876 - correct
         Events : 852736


      Number   Major   Minor   RaidDevice State
this     0       8        2        0      active sync   /dev/sda2

   0     0       8        2        0      active sync   /dev/sda2
   1     1       8       18        1      active sync   /dev/sdb2

lewinb@Poweredge:~$ sudo mdadm --query /dev/md0
/dev/md0: is an md device which is not active
lewinb@Poweredge:~$ 
```

So I guess my question is, why doesn't mdadm --assemble --scan work? what am I doing wrong here?


Edit ------------------------------------

I did more reading... It's not spelled out anywhere that you have to add raids to mdadm.conf manually... I checked it and there was nothing specific there. So I did this as root (wouldn't work as sudo):

```
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

That added the following at the end of the generic mdadm.conf file:

```

# This file was auto-generated on Wed, 24 Jun 2009 01:05:20 -0500
# by mkconf $Id$
ARRAY /dev/md1 level=raid1 num-devices=4 UUID=5d036ab1:6a62e860:809e6d1d:1dd1ea4d
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=ef6853e4:06b78687:9aa924e0:4d08f2c8



```

Shortly thereafter, "998.7 GB Media" shows up as a device in nautilus. It asks for authentication if I try to mount it... After a restart, it doesn't show back up. I had to do mdadm --assemble /dev/md0  to get it to show up again. And even then it said mdadm: device /dev/md0 already active - cannot assemble it. 

What gives? I'm not even sure what I did the first time that made it show up.

Both disks are full of data. Will I hose the data on these drives if I mount? I haven't done anything destructive to the data thus far, so I don't know if mounting would change anything.

I would GREATLY appreciate any knowledgeable help!!!

---

### Post by ronparent on 2009-06-27
Are your dives plugged into sata ports set as raid in bios? The raid in bios should NOT be turned on to use them in a software raid set.

It is possible using 9.04 for the raid to not automatically mount on boot. This problem has been adressed in the servers section of this forum and work arounds have been posted.

---

### Post by lewinb on 2009-06-28
Hi, thanks for the response!

I checked before doing much of this, and there isn't even a setting in BIOS for RAID. (odd for a server, don't you think?) The SATA port designations are either "auto" or "off". I think Dell intended that businesses buy one of their raid cards as an accessory to the server, instead of using software raid.

My big question, before I tell it to go ahead and mount the drive that shows up is: should/would this have any possibility of hosing the data that's there? 

At several points throughout working on this, I've shut down, taken the disks out, and put them back in the NAS just to check, and all the data seemed to be there. I would hate to get to this point without having screwed it up, and then lose everything!

---

### Post by ronparent on 2009-06-29
Your issues with the raid drives may be an ownership issue. Since they were originally installed and configured on another machine they were owned by that machine. I sense that you overcame that by operating on them as root. A chown command might correct that but I can't quote the syntax or what you would have to operate on.

I see no danger in simply mounting them if the forced recognition didn't hose them.

---

### Post by lewinb on 2009-07-29
Yes, I did have to change ownership of a number of directories (hmmmm... maybe all of them. Can't remember) from root to me. The NAS indeed operated on everything as root. And thankfully, none of this hosed the data. 

Here's what caused the problem for me: I mistakenly (apparently) thought that if Ubuntu recognized a device, it would (and should) automatically mount it. Not so. Even when it recognized the two drives as a raid, I still had to go in EVERY time, and mount it in the terminal. Irritating. And as far as I could tell, there's no GUI way to add something to fstab... Also VERY irritating. Please correct me if I'm mistaken about any of this. 

Out of curiosity, why *doesn't* Ubuntu auto-mount drives when it recognizes them... Or at least pop up a dialog asking what to do?

One thing I still don't understand is why Ubuntu doesn't show the device on the "Places" tab in Nautilus or Thunar, as a separate filesystem. When I mount other drives as external drives, they show up there, so why doesn't this? I put it in fstab at /mnt/raid, so it is permanently mounted at startup. It seems counterintuitive to me that I have to dig down in the filesystem of my startup drive to get to a totally separate filesystem on another device. Yes, I know there's some explanation about /mnt/raid only being a mount-point where ubuntu looks to find the actual device, but nonetheless, shouldn't it show up in the GUI?

---

### Post by frunns on 2009-07-29
I suppose it's the same in the server and the desktop versions. Ubuntu checks /media for drives mounted and shows them in places, don't think it checks /mnt any more.

There ARE ways to add to fstab with a GUI, not sure about raid-devices though. Personally I use Pysdm.

---

### Post by lewinb on 2009-07-30
If I add the mount the raid in /media instead of /mnt , won't ubuntu regard it as removable? That's where everything else I've plugged in has shown up.

---

