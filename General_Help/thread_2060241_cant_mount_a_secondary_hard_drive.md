---
title: "cant mount a secondary hard drive"
date: 2012-09-19
forum: General Help
---

### Post by bullfrog1979 on 2012-09-19
Hello everyone,

I'll start by saying I'm brand new to Ubuntu.

everything work fine after the install.  I've added a second hard drive (ext2) that was in a small NAS.  I need to get all of the data off of it but cant figure out how to mount it so I can access it.

using Gparted I can see the drive and it's partitions but cannot mount it.

any help would be hugely appreciated

thanks.

---

### Post by critin on 2012-09-19
Open disk utility. Click on the drive you want to bring it into focus.  Then look for the 'mount volume' text to mount it.  You should then find it in your file manager, home folder.  It will be along the side bar in  file manager.

---

### Post by bullfrog1979 on 2012-09-19
thanks for the info.

I guess I should have mentioned the disk was part of a raid array.  the partition i need access to will not mount.

is there any ways around this with out having to format the partition?

---

### Post by Bucky Ball on 2012-09-19
If the partition you want to mount is sdb1 (check in gparted) then:

```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```

That *should* do it. You may need to change some of the details to match your situation. They can all be found in Gparted or by running:

```
sudo blkid
```

---

### Post by bullfrog1979 on 2012-09-19
thanks, the result I get is

mount: unknown filesystem type 'linux_raid_member'

after run blkid

UUID="******" TYPE="linux_raid_member"

in Gparted it's listed as ext2

---

### Post by cprofitt on 2012-09-19
If the disk was part of a raid array -- then you may not be able to get the data. It would depend on the raid level used (how the data was stripped).

Is the NAS device still available?

Do you know what raid level was used?

Do you know if it was hardware or software raid?

---

### Post by bullfrog1979 on 2012-09-19
it was a mirror.  the NAS is toast and the second HDD's motor is dead.

---

### Post by cprofitt on 2012-09-19
You should be able to do it then...

If you have a spare disk you might want to make a complete clone of the disk you are going to try and access.

Do you know if the NAS was using hardware raid or software? What kind of NAS was it?

---

### Post by bullfrog1979 on 2012-09-19
ok got it mounted but here's my next problem->

on the partition (with hidden files shown) there are only a couple files totalling 33 meg.

there is over 450 gig of data on that partition, Gparted shows 450 gig used as well

it was a D-Link DNS-323 NAS

---

