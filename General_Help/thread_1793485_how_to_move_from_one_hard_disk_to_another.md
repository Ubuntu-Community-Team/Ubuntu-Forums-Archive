---
title: "how to move from one hard disk to another"
date: 2011-06-29
forum: General Help
---

### Post by Archy1987 on 2011-06-29
Hi! I have installed ubuntu on my 40 gb hard drive. I bought 160 gb hard drive and now i want to move ubuntu installation from 40 gb drive to 140 gb drive. How to ?

---

### Post by wolfen69 on 2011-06-29
You could use Clonezilla to make an image of your hard drive then transfer it. [Here]("http://clonezilla.org/clonezilla-live.php") is the Clonezilla live cd.

---

### Post by Archy1987 on 2011-06-29
> **wolfen69 said:**
> You could use Clonezilla to make an image of your hard drive then transfer it. [Here]("http://clonezilla.org/clonezilla-live.php") is the Clonezilla live cd.
Ok, i cloned partition with CloneZilla, but now i have one problem - there is 120gb of space on my hard drive, that is not used. How to combine it to make one partition 160 gb ? See attached image.

---

### Post by steve7777777 on 2011-06-29
To expand the partition use Gparted.

---

### Post by seawolf167 on 2011-06-29
> **Archy1987 said:**
> Ok, i cloned partition with CloneZilla, but now i have one problem - there is 120gb of space on my hard drive, that is not used. How to combine it to make one partition 160 gb ? See attached image.

Boot off a Ubuntu Live CD (your partition needs to be unmounted), then fire up GParted and resize the partition(s) to fill your unallocated space.

---

### Post by Archy1987 on 2011-06-29
> **steve7777777 said:**
> To expand the partition use Gparted.
Well, i opened Ubuntu Software Center, i searched for "Gparted" - i found it, and when i pressed button to open it, everything i get, was just a blank window. Why? See attached.

---

### Post by seawolf167 on 2011-06-29
GParted should be on the LiveCD already - System -> Administration -> GParted. If it is not, you can always use the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php").

---

### Post by Archy1987 on 2011-06-29
Ok, i googled for solution, and i found it - 

sudo apt-get install gparted

But how to combine those two partitions into one unit?

---

### Post by mikewhatever on 2011-06-29
You have the root, the swap, and the data partition. Which one of them is not used, and why do you think so?
It's been mentioned quite a few times above, and yet again, you have to use the Live CD to manipulate partitions.

---

### Post by seawolf167 on 2011-06-29
I would delete the swap partition and the 140GB ext partition (which is empty right?), then resize your current partition (40GB) into the unallocated space and recreate the swap partition at the end of the table.

Notes:
-the partition has to be unmounted to work on it
-swap partition should be created as type linux-swap
-you may (probably will) need to edit your /etc/fstab entry on reboot and edit your swap entry

---

### Post by Archy1987 on 2011-06-29
Thank you. I did what you said. Is everything OK now? Do i need to create the swap? - see attached image

This is my fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fb70ff07-6e27-47a3-9edc-2dedee03f514 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5e664a34-f425-4f79-b268-8a21230786c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by -kg- on 2011-06-29
My suggestion would be to make sure you have no data in your data partition (1.94 GB used might be a bit more than overhead), delete the data partition (if you don't want it), move the swap all the way to the right, and expand your root partition into the free space.

If you need help with partitioning operations, read at the link in my signature block.

---

### Post by Archy1987 on 2011-06-30
> **-kg- said:**
> My suggestion would be to make sure you have no data in your data partition (1.94 GB used might be a bit more than overhead), delete the data partition (if you don't want it), move the swap all the way to the right, and expand your root partition into the free space.

If you need help with partitioning operations, read at the link in my signature block.
read my post above. i did it already. But do i have to create a swap? What is swap? Why do i need it ?

---

### Post by DawieS on 2011-06-30
You will only need **Swap** space if you make use of the (power saving) hibernation utility, or if your computer has less RAM installed than required by the programs you use.

I find the hibernation function useful, in that I sometimes forget to shut down my computer, then it hibernates after 1 hour of no activity. Otherwise it would still be running the next morning.:eek:

The swap partition should be at least the same size as the RAM installed in your computer.

---

### Post by moonport on 2011-06-30
> **-kg- said:**
> My suggestion would be to make sure you have no data in your data partition (1.94 GB used might be a bit more than overhead), delete the data partition (if you don't want it), move the swap all the way to the right, and expand your root partition into the free space.

If you need help with partitioning operations, read at the link in my signature block.

Thanks, KG. Your link was useful for me 2.
Best.

---

### Post by steve7777777 on 2011-06-30
> **DawieS said:**
> You will only need **Swap** space if you make use of the (power saving) hibernation utility, or if your computer has less RAM installed than required by the programs you use.

I find the hibernation function useful, in that I sometimes forget to shut down my computer, then it hibernates after 1 hour of no activity. Otherwise it would still be running the next morning.:eek:

The swap partition should be at least the same size as the RAM installed in your computer.

More on swap [here]("https://help.ubuntu.com/community/SwapFaq"). As a rule I use swap for the primary drive only.

---

