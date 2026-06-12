---
title: "DD and cloning external harddrives of different sizes"
date: 2010-02-17
forum: General Help
---

### Post by IQAndreas on 2010-02-17
I'm not sure if this is the right area for this question, but I'll give it a go.

In the past, I have used dd to replace (as well as overwrite) hard drives.

If you do a direct clone of a drive, you are supposed to make sure the target drive is the same size as the source drive. 

It is quite important that I am able to clone a failing drive (250GB), however, my only other drive available is a completely new 1TB external hard drive from a different manufacturer.

**Is it still possible for me to safely clone the failing drive? If yes, how would I go about doing this?** Make a 250GB partition on the 1TB drive? 


If I use the TB drive as a "temporary backup", and once I have copied over with dd burn everything directly to DVDs, and then restore the TB drive to it's original state, will this be able to be done?

---

### Post by megamania on 2010-02-17
If you're going to make a bit-by-bit copy, you don't need to make any partition on the target drive, which will become an exact copy (also in "virtual" size) of the source.

When you say "failing", what do you mean exactly? If you can still read it, I'd suggest a file-by-file copy using rsync.

Also, take a look at Clonezilla.

---

### Post by Nostalos on 2010-02-17
I agree, if its readable file copy with rsync or other utility would be the easiest bet.

if you must do a bit by bit copy then you would need to grab the whole disk rather than just a partition. 

example instead of 
```
dd if=/dev/sda1 of=/dev/sdb1
```

use
```
dd if=/dev/sda of=/dev/sdb
```

this would leave your 1TB disk with a partition the exact size as the old 250GB disk and 750GB of free space.  Which if it is a resizable filesystem such as ext3 or ext4 you can then use gparted to change the size of the partiion to the full 1TB and extend the filesystem to utilize it.


Also on another note, if the disk is failing and you have bad sectors you may want to use something like ddrescue which does not error out on unreadable sectors.

---

### Post by IQAndreas on 2010-02-23
Hm... I was supposed to get email notifications of replies... I need to recheck my settings. [/thinkoutloud]


Thanks for the input guys. :)

Yes, the drive is completely failing. It makes horrible clicking noises, and before it died it had crashed once already, but I was able to restore much data with chkdisk. However, this last time it failed miserably, and is no longer readable or repairable via chkdisk.

I'm still kicking myself for procrastinating to backup the data while I had the chance. :(

> **Nostalos said:**
> Also on another note, if the disk is failing and you have bad sectors you may want to use something like ddrescue which does not error out on unreadable sectors.
Perfect! I was planning on using regular dd and tell it to keep going and ignore all errors (I'm pretty sure there is a flag for that), but ddrescue is just what I need.

Since I'm running in Ubuntu anyway, is there any GUI for ddrescue? I prefer having all options available and visible to me instead of digging through the docs and hoping to God that I didn't misspell anything. ;)



One final thing, sadly, I had to start using the harddrive already due to another system that needed a fresh reinstall and I needed somewhere to backup the existing contents.

Sorry for being difficult, but is there any way to preserve what is already on the external drive when restoring bit by bit?



[SIZE="1"]When I'm on the ActionScript forums, I am in control and on top of it all. Here I feel so helpless... :([/SIZE]

---

### Post by Nostalos on 2010-02-23
There is no GUI for ddrescue, but then again there is not many commandline arguements for it.

[http://www.forensicswiki.org/wiki/Ddrescue](http://www.forensicswiki.org/wiki/Ddrescue)   has some examples.

> 

One final thing, sadly, I had to start using the harddrive already due to another system that needed a fresh reinstall and I needed somewhere to backup the existing contents.

Sorry for being difficult, but is there any way to preserve what is already on the external drive when restoring bit by bit?


Nope.


P.S.  there are 2 packages in the repositories.  ddrescue and gddrescue.  you want gddrescue.

---

### Post by Nostalos on 2010-02-23
Had another thought as well.  can use ddrescue to output to a file instead of another physical disk.   Not sure of the syntax off the top of my head but you can then mount the file as a virtual disk in Ubuntu and recover the contents that way.  As long as you have enough free space on the destination drive you can copy the entire 250GB partition bit by bit to the existing file system.


```
ddrescue --no-split /dev/hda1 /path/imagefile /path/logfile 
```

then as root (note this is from memory so may not be 100% correct)

```
 sudo mount -t ext4 -o loop /path/imagefile /mnt
```

provided its ext4 filesystem.

---

### Post by oldfred on 2010-02-23
I do not think you want to use dd to copy from a small disk to a large one. There was a previous thread were someone did that and his new large drive was set to be the small drive size. Nothing worked to resize the drive until he downloaded a utility from the drive mfg. Another thread had the same issue but the brand of drive had no utility.

---

