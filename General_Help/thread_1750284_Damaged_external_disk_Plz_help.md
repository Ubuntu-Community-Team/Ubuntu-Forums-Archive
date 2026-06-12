---
title: "Damaged external disk: Plz help"
date: 2011-05-05
forum: General Help
---

### Post by astrobob.tk on 2011-05-05
Hello guys,

I have this external hard disk drive (Toshiba, Model: HDDR400E03X; 400GB). It fell on the ground & doesn't seem to be detected on neither Win or Linux.

It was sent to a computer company (they claim to recover data from damaged disks) in an attempt to recover the data. It was returned with no recovered data.

I was wondering if this community can help me with this & be able to recover any amount of data from it.

i tried the following:

```
sudo fdisk -l
``` but got nothing except the internal HDD which is /dev/sda

& ```
sudo lshw -C disk
``` but nothing additional to when the disk was unplugged.

any help is appreciated!!!

P.S.: the drive's light goes on when plugged & the disk is hear as spinning though with a scratchy noise every now & then. Moreover, there seems to be a loosened part inside since when shacked a sound is heard.

---

### Post by dragonfly41 on 2011-05-05
Most of the posts here on data recovery do not refer to physical damage such as the "drop test"

[http://www.wikihow.com/Recover-a-Dead-Hard-Disk](http://www.wikihow.com/Recover-a-Dead-Hard-Disk)

Since there are "scratchy" noises coming from the damaged (dropped) disk your first priority should be to try to clone a copy of the entire damaged disk image onto a healthy external drive .. e.g. 800 GB USB drive (at least twice as large as your damaged drive).

However you say that only the internal drive is recognised.

Partition the new external drive into two partitions .. same format as your damaged disk.

Use clonezilla (e.g. on parted magic or other rescue disk) or dd command (search this forum) try to clone from your damaged drive into one of the external formatted partitions.

Test to see if your cloned disk can be mounted. 

If not .. use testdisk and photorec to try to recover any files from the cloned partition into the second partition on the external drive.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

But search the forum .. there are many posts .. but usually not due to a dropped drive unfortunately.   

You might be lucky but minimise the handling of the drive (like shaking it !) until you have cloned it.


[EDIT]  Since it is already an external drive it may be that the damage is to the enclosure and not the drive itself.

If there is serious physical damage the chances or recovery are very slim but not impossible .. depending on how important your data is.


[FURTHER EDIT]

The chances of recovery are virtually nil if the disc was spinning when it was dropped.

I've never tried the following trick .. which is to be used as a last resort and at your own risk .. but I've read in threads like this ..

[http://ask.metafilter.com/28159/Help-I-dropped-my-external-hard-drive](http://ask.metafilter.com/28159/Help-I-dropped-my-external-hard-drive)

that occasionally discs damaged by being dropped can be temporarily fixed by wrapping the drive in a plastic bag (watertight) and then placing in deep freezer for some hours.

The theory seems to run that any cracks in circuit boards due to being dropped might contract (bridge the crack) when frozen and make a temporary connection.

But if you are desperate enough to try this trick  .. you must have a backup disk at hand to immediately clone the contents before the drive thaws out.   You only have one go with this trick.

Sounds a whacky idea but several posts I've read refer to this trick working.

More here on other recovery approaches ..

[http://xytron.co.uk/blog/?p=46](http://xytron.co.uk/blog/?p=46)

---

