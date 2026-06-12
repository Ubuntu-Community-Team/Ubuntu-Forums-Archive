---
title: "How do I Mount Raid1 at Startup"
date: 2011-09-26
forum: General Help
---

### Post by sibleytr on 2011-09-26
Have a lucid (10.04) desktop system that was just built using an alternative cd to create software RAID1.
RAID1 is 2 x 500GB drives with two partitions for / and swap.

md0 - is /
md1 - is swap


From the Desktop used System > Administration > Disk Utility
Create RAID1 software RAID with 2 x 2TB hard drives. At this time I can only start and access the RAID1 by using the Disk Utility.

Level: Mirror (RAID-1)
Name: r1v1
Label: vol1
Device: /dev/md2p1
Mount Point: /media/vol1
Partition Type: Empty (0x00)

Added to mdadm.conf:
ARRAU /dev/md2p1 level=raid1 num-devices=2 UUID=d2f16473-9441-4d19-bd0f-7f177cd83101

Tried 1 and 2 in fstab with no luck:
# vol1 is /dev/md2p1
# Try 1 - [COLOR="RoyalBlue"]UUID=d2f16473-9441-4d19-bd0f-7f177cd83101 /media/vol1     ext4    defaults        0       0[/COLOR]
# Try 2 - [COLOR="RoyalBlue"]/dev/md2p1 /media/vol1     ext4    defaults        0       0[/COLOR]

On start up I get "The disk drive is not ready yet or not present". From what I am able to diagnose, the RAID is not starting and thus I am unable to mount the RAID because it is not available until I start in from the Disk Utility.

Any ideas why am unable to mount the md2p1 at startup?

---

### Post by sibleytr on 2011-09-28
Ok - Figured it out:

After going through numerous web sites here is what I have. In a nut shell my end result looks like the above listed "Try2". The only thing different was I created the RAID1 using the mdadm command and named the array md2 as opposed to the Disk Utility application naming it md2p1.


mdadm.conf
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=84cd6c5c:96eb1eab:f3e63d43:e19b6823
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=6e9c4a1a:6c7f049f:ae6c2416:3b7d8297
[COLOR="Red"]ARRAY /dev/md2 level=raid1 num-devices=2 UUID=fd428280:8766de31:929d5314:6c82ef07[/COLOR]

Both md0 and md1 reside on the same array set, separate partitions, and were created using the Alternate Live CD during the original server creation.
md0 - the root array - /
md1 - the swap array - swap
[COLOR="red"]md2 - the array that was added to the server after its creation - /mnt/vol1[/COLOR]


fstab
# /md0 - root
UUID=058e6e84-feaf-4e4c-9fe3-9a64b3d8c5ab / ext4 errors=remount-ro,user_xattr 0 1
# /md1 - swap
UUID=33d144ae-a769-4ce2-b122-e9a847f2e7c5 none swap sw 0 0
[COLOR="red"]# /md2 - vol1 array
/dev/md2 /mnt/vol1 ext4 defaults 0 0[/COLOR]


The array is detected and mounted at start up. What I have not figured out, was creating the array using the Terminal the answer or did I just not have my mdadm.conf configured correctly when the array was created using the disk utility.


This one is for all of the newbies out there (like myself), who are trying to determine if Linux is functional and FRIENDLY enough to leave Windows.

---

