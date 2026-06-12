---
title: "mount second drive"
date: 2011-02-08
forum: General Help
---

### Post by snorkytheweasel on 2011-02-08
"Old" disk was the primary - and only - drive. 500 GB.

I have to move that drive to a new machine off-site, so I'd like to get the 10 or so GB of data from it and put the data on a "new" drive - 80 GB, with an existing maverick installation.

I tried to use Acronis to create an image. That way, the new drive would be  a clone of the old drive, other than being much smaller. Acronis wouldn't allow it because of the size difference.

When booting to the "new" sda everything works ... except that maverick "sees" sdb, but won't let me access the data partition sdb2.
[LIST]
[*]disk utility "sees" sdb and describes it as having boot partition sdb1, and the other 499 GB , sdb2 (and sdb5)
[*]nautilus and dolphin both "see" sda and can access all of the data (such as it is, given that it's a new installation)
[*]nautilus and dolphin both "see" sdb, but only access the 255 MB boot partition sdb1
[/LIST]
I tried doing a clean install on the "new" drive. In that install I left the old drive in place as a second drive - hoping that the installation would recognize it as a second drive and mount it properly. However, 1) it didn't do anything with  the old drive and 2) the results are the same - no access to the data partition on the "old" drive.

I think the problem is that I need to mount  sdb2, but I can't figure out how. Here is the information from fdisk:

[FONT="Courier New"][B]sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8455

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          32      248832   83  Linux

Partition 1 does not end on cylinder boundary.
/dev/sdb2              32       60802   488134657    5  Extended
/dev/sdb5              32       60802   488134656   8e  Linux LVM[/B][/FONT]

This is this contents of fstab:

[FONT="Courier New"][B]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=60da3f80-433a-4311-b5aa-a1f14255cc2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9ff62360-8078-4c71-b21e-26af4ea5e3ce none            swap    sw              0       0[/B][/FONT]

Do I enter information in fstab to enable mounting? If so, which information do I use?

Or is there another way to access the 10 GB of data on sdb  and get it on to sda?

By the way, in the course of messing with this, I managed to make the "old" drive unbootable, so I can't just reverse the drives' roles. The "old" drive has the boot partition marked as bootable, and I switch drive jumpers (and cable setup), but that doesn't help.

Now what?

---

### Post by mantaboo on 2011-02-08
perhaps you can try:
```
mount /dev/sdb2 /mnt/sdb2
```

---

### Post by snorkytheweasel on 2011-02-08
> **mantaboo said:**
> perhaps you can try:
```
mount /dev/sdb2 /mnt/sdb2
```

BASH returns:
[FONT="Courier New"]mount: mount point /mnt/sdb2 does not exist
[/FONT]

---

### Post by dino99 on 2011-02-08
with both hdds plugged, use gnome commander to copy your data from one to the other

---

### Post by snorkytheweasel on 2011-02-08
> **dino99 said:**
> with both hdds plugged, use gnome commander to copy your data from one to the other

Just like nautilus & dolphin, commander can't see sdb2.

Perhaps I didn't understand your suggestion?

---

### Post by mantaboo on 2011-02-08
sorry :
```
sudo mkdir /mnt/sdb2
```then:
```
sudo mount /dev/sdb2  /mnt/sdb2
```then see if the mounted partition shows up in the file manager or you can:
```
ls /mnt/sdb2
```to see if you can access them from  within the terminal. Let us know if that works. If it does we can edit your fstab to mount it automatically on boot.

---

### Post by Morbius1 on 2011-02-08
sdb2 is an extended partition not a logical or primary partition. Nothin' to see there:
> [FONT=Courier New]** /dev/sdb2              32       60802   488134657    5  Extended**[/FONT]

---

### Post by mantaboo on 2011-02-08
Do you have another suggestion?

---

### Post by snorkytheweasel on 2011-02-24
> **mantaboo said:**
> perhaps you can try:
```
mount /dev/sdb2 /mnt/sdb2
```

That wasn't exactly correct, but it was close enough. It's working now.

---

