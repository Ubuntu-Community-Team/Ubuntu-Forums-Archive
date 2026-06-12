---
title: "Seriously confused about partitions"
date: 2010-01-26
forum: General Help
---

### Post by Iskalla on 2010-01-26
I currently have a partition dedicated to Vista and a partition for Ubuntu, only I haven't used Vista in as long as I can remember and have no intention of doing so any time soon. I want to format vista, merging it into Ubuntu. However, I have also created a partition for Root and Home, 11gb and 76gb, thinking back I should have just put Ubuntu altogether on one partition, I intend on installing more software in the future an it appears my current root partition isn't enough. Other than starting from scratch and losing everything, I can't think of how I can tidy everything up, I don't want to be restricted in how much software I can install, but as long as Root is in a separate partition it looks like I'm stuck. I have no idea where to begin...

---

### Post by chewearn on 2010-01-26
Post the output of:
```
sudo fdisk -l
```

Or run Partition Editor and post a screenshot, so that we can understand your current set-up.

---

### Post by earthpigg on 2010-01-26
note the sizes of the various partitions, to ensure you don't erase the wrong one. back up all your vital data -- if a partitioning operation goes wrong, its likely you will fry your install and need to do a complete reinstall... a power outage in the middle of this, for example, could result in that. so could accidentally hitting 'apply' before double and triple checking what is on the screen.

boot an ubuntu live cd.

run the partition editor from the live cd.

delete the windows partition.

resize the root partition. 20gb should be fine, but you can go larger if you like.

resize the home partition to take up the rest of the space.

you may have fstab problems upon rebooting. before starting, you can run this command from your install (not from the live cd) and show us the output and we can tell you if you will or wont:

cat /etc/fstab


edit: whoops, do what these other two posters are suggesting before starting. im assuming we understood your partition scheme exactly correctly, which we may not. better safe than sorry.

---

### Post by ChrisB111 on 2010-01-26
I don't know much about partitions but **beware** anything you do with partitions can, in a worst case scenario result in a total loss of data. Make sure you have recent backups when you edit partitions.

Chris

---

### Post by Iskalla on 2010-01-26
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefff69d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       12448    98444288    7  HPFS/NTFS
/dev/sda3           12449       22277    78951442+   f  W95 Ext'd (LBA)
/dev/sda4           22278       24321    16418430   83  Linux
/dev/sda5           21699       22232     4280468+   7  HPFS/NTFS
/dev/sda6           22232       22277      364240+  83  Linux
/dev/sda7           12449       21698    74300562   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 127 MB, 127582208 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x018fcbb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          16      124560+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(14, 254, 63) logical=(15, 130, 19)

--

I think there are also a few gig's worth of other partitions for file storage that got created in the process of installing Ubuntu that I would ideally like to remove. This was a first for me, and although everything is working fine it hasn't been the tidiest installation.

---

### Post by uncle-c on 2010-01-26
You can download the latest gparted live cd : [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

and use it to delete your vista partition and resize any other partitions that you may have ( including /root and /home ). Backup any valuable data just in case.

---

### Post by earthpigg on 2010-01-26
im just putting this in code tags so we can read it easier.

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefff69d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       12448    98444288    7  HPFS/NTFS
/dev/sda3           12449       22277    78951442+   f  W95 Ext'd (LBA)
/dev/sda4           22278       24321    16418430   83  Linux
/dev/sda5           21699       22232     4280468+   7  HPFS/NTFS
/dev/sda6           22232       22277      364240+  83  Linux
/dev/sda7           12449       21698    74300562   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 127 MB, 127582208 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x018fcbb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          16      124560+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(14, 254, 63) logical=(15, 130, 19)

```

can we see the output of this command, too?

cat /etc/fstab

---

### Post by Ginsu543 on 2010-01-26
If you plan on sticking primarily with Ubuntu and upgrading to new releases in the future, it is actually a good idea to have / and /home separate. It will make the upgrade process much easier since you can install the new version over the old version without formatting the /home directory, which will save all the settings/customizations you made so you don't have to do it all over again.

Having said that, you may be able to use Gparted to format your Vista partition to ext4 (or whatever format you used for your Ubuntu partition) and then resize your / and /home partitions. This is by definition a risky procedure, so I would back up all your important data before proceeding.

All else fails, you could just start over and do a fresh reinstall. One of the beautiful things about Ubuntu is that it doesn't take forever to install (or reinstall). I've had to do fresh reinstalls several times because I borked the system (e.g., trying out different video drivers). I have my data backed up, so no worries. Each time, I had my system back up and running in less than an hour.

---

### Post by Iskalla on 2010-01-26
I'm assuming the root partition is a necessity, if so, is it possible to use the space currently used by vista and merge it into root and home accordingly, and repeat this in the future if needs be? That would be ideal. Everything is backed up, my main concern isn't so much data loss but having to configure everything from scratch after getting it to a point that I'm comfortable with, hopefully it shouldn't go that bad though. I'm gonna start by removing vista anyway and work from there.

---

### Post by Iskalla on 2010-01-26
> **earthpigg said:**
> im just putting this in code tags so we can read it easier.

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefff69d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       12448    98444288    7  HPFS/NTFS
/dev/sda3           12449       22277    78951442+   f  W95 Ext'd (LBA)
/dev/sda4           22278       24321    16418430   83  Linux
/dev/sda5           21699       22232     4280468+   7  HPFS/NTFS
/dev/sda6           22232       22277      364240+  83  Linux
/dev/sda7           12449       21698    74300562   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 127 MB, 127582208 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x018fcbb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          16      124560+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(14, 254, 63) logical=(15, 130, 19)

```can we see the output of this command, too?

cat /etc/fstab
```

james@iskalla-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=6b8349e7-af0d-45ea-9bba-751391f92ae7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=669c5507-f261-4077-8727-a7634c67bd48 /home           ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by ibuclaw on 2010-01-26
Added code tags, so everyone can read it without struggle. :)

---

### Post by ibuclaw on 2010-01-26
> **Iskalla said:**
> ```

james@iskalla-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=6b8349e7-af0d-45ea-9bba-751391f92ae7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=669c5507-f261-4077-8727-a7634c67bd48 /home           ext4    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Only thing I have to add is this:

/ is /dev/sda4
/home is /dev/sda7

Vista is probably /dev/sda2

So what on earth is:
/dev/sda1
/dev/sda5
/dev/sda6


I suggest you simply things a bit here. :)

Also, you seem to be using ext4 partitions, resizing these partitions using gparted has proved to be troublesome in the past, leaving you with nothing but a corrupt filesystem(s).

Regards
Iain

---

### Post by Iskalla on 2010-01-26
> **tinivole said:**
> Only thing I have to add is this:

/ is /dev/sda4
/home is /dev/sda7

Vista is probably /dev/sda2

So what on earth is:
/dev/sda1
/dev/sda5
/dev/sda6


I suggest you simply things a bit here. :)

Also, you seem to be using ext4 partitions, resizing these partitions using gparted has proved to be troublesome in the past, leaving you with nothing but a corrupt filesystem(s).

Regards
Iain

I believe those partitions were created for some reason or another during installation and now serve no purpose, I'm sure they are under vista so they'll be removed anyway. I had a lot of problems selecting a file system during installation that would work, I tried installing from windows initially with no luck and then from the disk, ext4 just worked.

---

### Post by Iskalla on 2010-01-26
Apologies for double post, but further confusion:

According to gparted, my root partion is 15gb with just 3gb used, in folder view it is 11gb with 5gb used, which also conflicts with the low space warning I had received earlier...argh, this makes no sense.

--

Ok then, this was my mistake, I was misreading...

---

### Post by bryanl on 2010-01-26
A first concern is the reluctance to refresh. One of the great things about Ubuntu is that it is fairly easy to totally reinstall a new and updated system yet keep settings and user stuff. What this means is being able to preserve the home directory and keeping track of how to refresh any special software not available in various repositories. 

That is why the suggestion above for a root and home 2 partition scheme works well (plus a swap partition unless you want to create and use a swap file). That way you can do a new install by wiping root and leaving home alone.

15 GB should be plenty for the root, everything besides home, partition. If you start getting low space warnings for this partition, something went haywire. The space needed for applications is usually in the megabyte range, if that, so installing them is seldom a space problem unless you are installing thousands. Log files or other temporary files might be a space problem but shouldn't be in normal use. The easiest way to fix unobvious haywire problems is a reformat reinstall.

Yeah, problems arise with a refresh sometimes. I've had network driver regressions and upgrade plugin coordination hassles and some other headaches on occasion but, overall, a clean system reinstall with a restored or kept home partition has worked well.

I have a page or two of notes that I use to cut and past for apt-get software installs and configuration file snippits to get a new system going just they way I like it with minimal hassle. (that's also a good way to find out how Ubuntu changes their package defaults from version to version, too!).

---

