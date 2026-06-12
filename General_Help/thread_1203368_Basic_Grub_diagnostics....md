---
title: "Basic Grub diagnostics..."
date: 2009-07-03
forum: General Help
---

### Post by SteveDee on 2009-07-03
Some common problems experienced with booting Ubuntu include Grub errors 15, 17, 21 & 22, and also booting to an apparently blank screen.

Here are some suggestions.

Boot your system from a Ubuntu CD (or USB stick) and explore the Ubuntu hard drive.
In the /boot directory you must have the following:-
 - a "grub" directory
 - a Linux kernel; this will have a name like vmlinuz-{version}-generic. For example; vmlinuz-2.6.28-13-generic
 - a ramdisk image; this will have a name like initrd.img-{version}-generic
Make sure you have a "pair" of these files (i.e. both files have the same version text) and note the full name of each.

Now go to /boot/grub on the Ubuntu hard drive and ensure you have the following:-
 - menu.lst
 - device.map
 - stage1
 - stage2

Your copy of menu.lst has been customised (possibly corrupted) so let us initially start again by creating a very simple configuration. This will give you a feel for your particular problem and also prove that your system will boot.

Make a backup copy of menu.lst

Delete everything from menu.lst and type the following with details to suit your system:-

title		{any text you like}
root		{enter the boot disk and partition. If you don't know what it is, open the device.map file and try the first identity in the form "(hdx,y)" where "x" is the drive and "y" is the partition}
kernel		{enter the Linux kernel path+file name noted above. Also enter the mount point for the Linux drive, which you may be able to work out by running the Partition Editor (GParted) from the LiveCD} 
initrd		{enter the ramdisk image path+file name as noted above}

Here is a menu.lst example:-
title		Larry Linux
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sdb1 ro 
initrd		/boot/initrd.img-2.6.28-13-generic

Having saved this in /boot/grub/menu.lst now reboot from the hard drive. 

Hopefully your system will display the Grub menu and from there you can boot "Larry Linux"....however, if you get problems:-

 - Error 15: this means that one of the files you specified (e.g. vmlinuz or initrd.img could not be found). So recheck the file names you entered are correct and located in the /boot directory.

 - Error 17: this means that the specified root drive (hd1,0 in the example) does exists, but you have specified the wrong partition. So try another partition (e.g. hd1,1). Remember that these numbers are base 0 (1st partition is 0 not 1).

 - Error 21: this means the specified root drive does not exist. Oh dear! Try another drive if there is another listed in the device.map file.

 - Error 22: this means the specified partition does not exist. Remember that these numbers are base 0 (1st partition is 0 not 1). Try other partitions on hard drive.

 - Boots to a blank screen: Grub is happy with you information, but the Linux kernel has probably been given the wrong mount point. Recheck the "root=/dev/xyz" details.

If you are able to get your system to boot (and armed with your new experience) you may be able to spot the problem in your original menu.lst file.

---

