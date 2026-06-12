---
title: "mdadm fails to start /dev/md0 array on boot"
date: 2009-12-23
forum: General Help
---

### Post by BeastlyKings on 2009-12-23
When I start my box mdadm fails to start my linear raid array of 4 drives. If I do:
mdadm --assemble --scan

it tries to start /dev/md0 but says it failed because only 2 (sometimes it says 3) of the drives were avalible and it didn't have enough to start the array.
If I do:
mdadm --stop --scan
and then
mdadm --assemble --scan

it fixes the problem and starts the array with all 4 drives.

But this is still a problem because I don't want to have to do that every time I start my computer.

I tried adding those commands to run automatically when the computer starts, but I can't seem to get it right.


Oh, and when the problem occurs I can't do:
mdadm --stop /dev/md0
and then
mdadm --assemble /dev/md0

because it says there are no devices for /dev/md0, so the only way it works is if I scan, then it finds md0 somehow, and starts it with all 4 drives.


any ideas? I don't care how I do it, I just want the array to be started automatically at or after boot.

---

### Post by QrK0 on 2009-12-23
My suggestion is, if you can access the data, copy it to another place and then delete the raid and start to build a new raid. When the raid is stable again, restore the data you previously saved.

---

### Post by BeastlyKings on 2009-12-25
Thanks for the reply!
I actually just created this array, so it has no data yet, just some folders for mythtv's recordings and such.
I think I'll try that though, I'll rebuild the array after the weekend here.

Just some more specs, in case it helps, my system has 5 drives.
120Gb SATA
80Gb  IDE
80Gb  IDE
160Gb IDE
5Gb   IDE


I installed mythtv on the 5Gb drive, and made the array using the other 4, does the fact that one of them is SATA make a difference?

---

### Post by QrK0 on 2009-12-28
The partitions should be equal in space, so if you have 4 partitions about 80G and the raid level is raid-5, the available space will be 80x4-80=240G. With your disks, you will loose 40+80+80=200G (raid5).
And the raid will be faster than the slowest disk.

---

### Post by Fcon_Vpro on 2009-12-28
He is using linear raid and not raid5. So he wont lose any space, but he loses redundancy and speed.
Sure combining all the drives to form one giant partition makes life easier, but like I said there is no redundancy and if one drive fails, then you lose everything.
If you aren't using RAID5 or RAID6 (with equal sized drives as mentioned by QrK0), then rather use the drives as single drives with each their own partition.

---

