---
title: "mdadm can this be done.. 4 drives to 3?"
date: 2009-09-03
forum: General Help
---

### Post by aarons6 on 2009-09-03
i have an installed system, its karmic kubuntu 9.10.
right now i have 4 120gb drives..

/boot is md0 4 small partitions raid1
/ is md1 4 100gb partitions raid5

i plan on, in the near future moving to 3x250gb drives for my raid.

i was doing some testing, i cannot figure out how to make mdadm drop a drive.

is this possible???

i do not at the moment have space to install the 3 drives with the 4 drives and copy over the root partition.. so i need to do this live.

i already know how i can drop 1 drive at a time and update that way, but mdadm will still show a 4 drive raid5 setup.. this means i would need 4x250gb.

---

### Post by Nostalos on 2009-09-03
Don't think what you are wanting is possible.  Parity distribution gets calculated based on the number of drives in the Raid5 Array.  You can't go from 4 to 3 without building a whole new array.

---

### Post by tgrimley on 2009-09-03
I can't tell exactly what you're trying to do but you can probably do it.  

To remove a drive, you'll need to fail it, then remove it from the array.  You will be degraded (unprotected from drive protection for new writes, but you can still add the removed drive back later...) during this process, but then you can add two of the 3 drives from the new array, running that degraded by adding "missing" to the --create command, then the adding the disk and rebuilding later.

do a 
```
mdadm --manage /dev/md1 --fail /dev/sdX
```
and then a 
```
mdadm --manage /dev/md1 --remove /dev/sdX
```
which should show you running degraded.  add two disks for the new array and do a 
```
mdadm --create /dev/md2 --level=5 --raid-devices=3 missing /dev/sda1 /dev/sdb1 
```
or similar.  these are examples (from memeory.. may be wrong) so make sure you know waht you're doing since this is a dangerous option.  I've done it migrating from a 5x500GB raid5 to a 3x2000GB raid5 with no problems.

---

### Post by aarons6 on 2009-09-06
so you just run a 4 disk array with one drive missing forever?

it wont effect anything?

---

### Post by tgrimley on 2009-09-06
It will be degraded and slow and you will lose all data if you lose one drive.  So no. but if you're trying to migrate, you can do it.  

What are you trying to do?  If you're moving data, it's possible you can do this safely.  Please re-read my post.

---

