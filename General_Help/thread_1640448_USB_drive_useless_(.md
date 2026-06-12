---
title: "USB drive useless :("
date: 2010-12-07
forum: General Help
---

### Post by Darkness134 on 2010-12-07
Ok guys i think that this is fixable... hopefully. Anyways i was trying to install crunchbang to my flash drive. (thought it looked pretty sweet) Anyways when i used the universal usb installer, it didn't have persistence for the latest version. So i thought i should look at the crunchbang forums to see how they suggest to install it. This is what i found:

[http://crunchbanglinux.org/wiki/statler_usb_installation](http://crunchbanglinux.org/wiki/statler_usb_installation)

I followed the guide and now it works on my flash drive and i like it, so now i am going to download the older version, install it with persistence, and see if i can update from there instead. Well now gparted cannot recognize my flash drive's file system and also cannot unmount it to be reformatted. I tried to format it with the disk utility next and i got this error:

"An error occurred while performing an operation on "2.0 GB Filesystem" (Partition 1 of Kingston DT 101 II): The daemon is being inhibited"

Does this means its read only or something? There has to be a way to fix it, plz help :(

---

### Post by efflandt on 2010-12-07
If you install an iso on USB, your ability to do updates is going to be limited.  Even with persistence you will not be able to update things like kernel or video drivers or anything else during initial boot or that requires initramfs to remake a new boot image, because initial boot is from fixed existing files from the iso before persistent data is mounted.

So you can use persistence for settings (like timezone and network settings) and you can add programs and data.  But you cannot update anything having to do with booting without going through a bunch more work to make your own iso first with what you want on it.

Have you tried using gparted to create a new msdos partition table and then make a new partition?  I have had to do that often when I accidentally erase the entire USB instead of the partition when using Startup Disk Creator.

---

### Post by Darkness134 on 2010-12-07
Ok i tried making a new partition table, and it seems to work at first, but when i try to format it back to FAT32 (or any other) it just says:

"An error occurred while applying the operations"

I saved the details and if it helps, here is what it says:
 
GParted 0.5.1

Libparted 2.2

Create Primary Partition #1 (ext2, 1.86 GiB) on /dev/sdc  00:00:00    ( ERROR )
    	
create empty partition  00:00:00    ( SUCCESS )
    	
path: /dev/sdc1
start: 63
end: 3903794
size: 3903732 (1.86 GiB)
set partition type on /dev/sdc1  00:00:00    ( SUCCESS )
    	
new partition type: ext2
create new ext2 file system  00:00:00    ( ERROR )
    	
mkfs.ext2 -L "" /dev/sdc1
    	
mke2fs 1.41.11 (14-Mar-2010)
/dev/sdc1 is mounted; will not make a filesystem here!
========================================

---

### Post by Darkness134 on 2010-12-08
Hm, Disk Utility says that the format the filesystem on the drive is Linux, which i never heard of as a filesystem. Anyways for some reason i got it to format today, maybe i just needed to restart ubuntu first... weird. Anyways, problem solved, thank you.

---

