---
title: "recovering windows disk from ubuntu...Help Please"
date: 2009-11-16
forum: General Help
---

### Post by luke0927 on 2009-11-16
Looks like i have a failing windows drive....I plugged it up and can see it under /dev its /dev/sdc and sdc1.  I pulled it up with Gparted can't detect the filesystem....I wasn't able to mount it either anyone have anything i can try...what would be the correct way to mount it when ubuntu doesn't automatically see it?

---

### Post by Giblet5 on 2009-11-16
How did you determine that the Windows partition is /dev/sdc1?

Have you tried repairing that partition?

```
sudo ntfsfix /dev/sdc1
```

---

### Post by luke0927 on 2009-11-16
I added it to my current box with a usb adapter....sda1 is ubuntu sdb1 is my windows disk and this was the one that came up...

I put it back in the laptop and booted with the live cd a sudo fdisk -l shows it as /dev/sda1 and can see it is HPFS/NTFS and is 80gb

I tried to mount it with the live cd using mount -t ntfs /dev/sdb1 /mnt/ntfs when I do that i get /dev/sda1 doesn't have a valid NTFS

---

### Post by Giblet5 on 2009-11-16
Don't mount it. It's corrupted. Fix it first.

```
sudo ntfsfix devicename
```

---

### Post by luke0927 on 2009-11-16
> **Giblet5 said:**
> Don't mount it. It's corrupted. Fix it first.

```
sudo ntfsfix devicename
```

when and tried it said NTFS is corrupt run chkdsk...I'm booting to a windows disk to try and run it any other things i could try? will chkdsk run in ubuntu?


edit chkdsk said volume appears to have one or more recoveralbe problems....this is my work PC i would like to try and recover something before turning it over to IT casue they will just wipe it clean I had some configs i was actually building today that i wanted to try and pull off.

---

### Post by seeker5528 on 2009-11-16
If you have another hard disk you can wipe, the best option is to use ddrescue to clone the drive, then try to fix the clone. If you are able to fix the clone then you can either repeat the process for the original or copy the clone back to the original drive:

ddrescue *infile outfile*

: infile and outfile can either be a device or file, in case you want to make an image file of your disk or copy an image file back to a disk.

If you don't have a drive you can wipe, but you have one with enough free space to hold all the files, then testdisk would be the next best thing.

Mount the partition you want to copy stuff to, then run testdisk. Should give you the option to scan, when the results of the scan are showing, you should be able to select an item from a list and choose to browse files, and when browsing the files you should have the option to copy the files at which point you should be prompted to choose a destination, which brings up a file browser so you can browse for the directory you want to use. As long as you don't have testdisk write changes, the original will not be modified, so you can check the copied files to see if things look OK before deciding your next course of action.

Later, Seeker

---

### Post by luke0927 on 2009-11-16
thanks didn't think of that I have used ddrescue....it has booted it up and I've got most all important things off of it now...might try to make a copy just to have it cause IT will just put a new disk in....Its about time to start fresh again anyways.

---

### Post by blueridgedog on 2009-11-16
+1 for ddrescue, note that you do not need another disk, just enough space for the image.

You can:
```

ddrescue /dev/sdc1 sdc1image logfile
```

Where sdc1image will be a file on your system.

The full manual is worth a look:

[http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

---

### Post by luke0927 on 2009-11-16
why would it boot into windows now for a little bit but not mount from a live cd...I added an entry to etc/fstab and when I try to mount it it says "The device /dev/sda1 doesn't have a valid NTFS.  Maybe you selected teh wrong device or whole disk instead of a partition......"

When doing a fdisk -l thats the only NTFS partition?  I would think if windows is able to see it linux would be able to also?

---

### Post by seeker5528 on 2009-11-17
I've run into that before, could be signs of disk failure, could be the result of abnormal shutdown, or a hard lock while a disk write was in process.

Usually then I visit the site of the disk manufacturer and download their utility for checking the disk.

If that doesn't turn up anything it's copy everything to another drive.

Then boot into Windows and set it to scan for errors and try to recover bad sectors on the next boot, then reboot to let it check for errors.

If there are still oddities then I do a disk wipe with [dban](http://www.dban.org/), reformat, then copy everything back.

Later, Seeker

---

