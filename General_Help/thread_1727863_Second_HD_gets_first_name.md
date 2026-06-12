---
title: "Second HD gets first name?"
date: 2011-04-13
forum: General Help
---

### Post by Macamba on 2011-04-13
Hiyah,

The last couple of days I have been playing around with an extra internal harddisk. I got it working, and even edited my fstab so it would automount. For the record, I also automount a partition of my Windows system so I can listen to music. Today I started my system, and was unpleasantly surprised by the message that there was a problem automounting the drive. Some research learned me that /dev/sdb1, the new internal drive now goes by /dev/sda1, and my music partition should be mounted using /dev/sdb6 instead of /dev/sda6. 

Anyone care to comment why my original harddisk got the designation sdb and my new drive sda?

Macamba

---

### Post by poodoopealeoaph on 2011-04-13
I'm not too sure that I can really help with all of this but I have noticed with my systems that if you have any sort of external/slave drive, you will always be able to view and use the data right off of it like it is regularly connected. So, if you have it all set up correctly, you should be able to locate your music through a window and just make a shortcut to your music folder on your desktop and browse your music that way... sorry if this wasn't much help though... I'm just not a super computer guru... yet!

---

### Post by ankspo71 on 2011-04-13
Hi,
wow. I haven't heard of the main hard drive (or system partitions rather) becoming remapped/renamed before, but I have heard of this happening before with multiple data partitions.

This type of problem can be prevented (or at least hopefully prevented) if you mount your partitions using UUID's instead of device names (/dev/sdb3 etc). 

If you open the terminal and run this command:
```
sudo blkid
```
it will tell you a unique UUID for each partition.

You would then want to edit the fstab as follows:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
[COLOR="Red"]UUID=cdbf7ced-70fd-4579-b79d-2a30e242a263[/COLOR] /               ext4    noatime,data=writeback,barrier=0,nobh,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
[COLOR="Red"]UUID=417aa881-deb6-4355-9366-82699104625f[/COLOR] none            swap    sw              0       0


## Storage
[COLOR="Red"]UUID=18446634-de62-4a76-974d-4250fdd1aedd[/COLOR] /media/sdb6 xfs users 0 0
[COLOR="Red"]UUID=d3e8f150-3579-4973-b9f4-2a0773d993fd[/COLOR] /media/sdb7 xfs users 0 0
```
The above is a copy of my own /etc/fstab

Just to be on the safe side, open up your computer to make sure that no jumpers fell out of the hard drive (I'm using ancient hard drives so it's happened to me twice before), and make sure they are in the correct postitions. I also recommend making sure everything is correct in your bios too.

Hope this helps.

---

### Post by Macamba on 2011-04-13
Ankspo71,

So it is something that can happen? Well, then I have to write the UUID's in my fstab, wont't I. Thanks for the answer. Have a :popcorn: ;)

Macamba

---

### Post by ankspo71 on 2011-04-13
Hi,
From what I've been told, the UUIDs are a newer feature to identify partitions so that they don't get mixed up while mounting. The reason I haven't heard of the system partition getting mixed up is because Ubuntu now automatically assigns a UUID for the root "/" partition during the installation process. But now I realize that your windows partition is probably sda1 (not Ubuntu like I thought)

I've thought about it for a while and this is what I came up with:
If we were to mount, for example, /dev/sdb3 to /mount/sdb3 and /dev/sdb4 to /mount/sdb4 at the same time (without using a UUID), then there is nothing preventing /dev/sdb4 from being detected first, and from what I understand, when partitions are detected they get assigned the first /dev/name available. With a UUID, each partition is correctly identified and gets assigned to the correct device name (and correct mountpoint). 
Can anybody help verify this? :D

Here is a little more information on UUIDs
[https://help.ubuntu.com/community/Fstab#Device](https://help.ubuntu.com/community/Fstab#Device)
[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)
Hope this helps.

---

### Post by ankspo71 on 2011-04-13
I found it :D
> Linux now prefers to use UUID (Universally Unique Identifier), LABEL, or symlinks to identify media storage devices on a system. Directly using /dev/hd*# or /dev/sd*# is no longer preferred since these device assignments can change between system boots: 
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

