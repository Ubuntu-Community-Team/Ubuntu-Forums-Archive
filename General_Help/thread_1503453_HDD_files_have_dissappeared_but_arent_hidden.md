---
title: "HDD files have dissappeared but arent hidden"
date: 2010-06-06
forum: General Help
---

### Post by Haagimus on 2010-06-06
I have an external HDD which i keep all my movies and tv shows and whatnot on. I rebooted my laptop routinely and when the HDD reconnected it still has the same amount of disc space used up but in my movie folder only 221/1186 movies are showing up in nautilus. I opened KDirStat to check and all the movies are still on the HDD nothing has been erased. I have restarted the laptop, restarted the HDD, disconnected/reconnected the HDD, swapped USB ports. I don't think it matters but I have written a .sh script that generates a list of all the folders contents and outputs it to a .txt file. Even though the HDD is only showing 221 files the txt output has all 1186. does anyone have any idea why 800 files would just not show up in nautilus explorer?

Currently running:
Ubuntu 9.10
Nautilus 1:2.28.10ubuntu3

EDIT: I can still access and play every file that is not showing up by opening them through a media player such as VLC. Also when i Alt+F2 and type the directory and file name they still fill themselves in as normal also.

---

### Post by lavinog on 2010-06-07
Do any of the files start with a period?

---

### Post by Haagimus on 2010-06-07
none of the files are hidden. All of the files are unmodified .avi files. Like I stated previously they were there until I restarted the system and then they just disappeared from the folder. Only gone in the nautilus explorer. When I 'ls' in terminal I can see that some of the files have an an error

"ls: cannot access Bug.avi: Input/output error"

I cannot tell how many have the error, but they are the files that are no longer showing. When I try to output the file to a .txt they do not output with the error in the text file.

---

### Post by Haagimus on 2010-06-08
gonna go ahead and say this is solved. Through the terminal I used mv to trade the contents to a new folder figuring out exactly which files were messed up. The files somehow just got corrupted on a bad disc sector so nothing I can do about it. Oh well i still saved 1086 movies out of the folder

---

### Post by lavinog on 2010-06-08
Did you try using fsck (file system check) on the drive?
It could also be bad sectors like you mentioned, does the drive make any clicking noises?

---

### Post by Haagimus on 2010-06-08
there is no clicking so there are no physical faults with the drive, running e2fsck outputs this:

e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

running the command stated at the end of that message simply outputs the same exact message

and dumpe2fs /dev/sdc1 outputs this:

dumpe2fs 1.41.9 (22-Aug-2009)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.

I have exhausted all options i found online so unless someone can come up with something i have not tried its endgame. its no biggie as its only lost time since i can recover all the data with time, but further suggestions are always welcome.

---

### Post by lavinog on 2010-06-08
did you use sudo with e2fsck?

what about 
```

sudo fdisk -l /dev/sdc

```
see if it can detect the filesystem type.

---

### Post by Haagimus on 2010-06-08
yup ran e2fsck with the sudo prefix, when i run sudo fdisk -l /dev/sdc1 its an NTFS file system.

---

### Post by lavinog on 2010-06-08
> **Haagimus said:**
> yup ran e2fsck with the sudo prefix, when i run sudo fdisk -l /dev/sdc1 its an NTFS file system.
well that would explain why e2fsck didn't work.

There is ntfsfix.
I have never used it, and the man page claims that it is not a replacement for chkdsk.  You should find a windows computer and run a disk check from it.

---

### Post by Haagimus on 2010-06-09
I forgot that I had given all my movies to a friend with a same sized HDD so im just gonna recover the 50 or so files that I lost from him. It's no biggie, ill likely backup all the data to his HDD then reformat as ext3 to mitigate further FS type issues with linux OS and win FS. Thank you everyone for all the help on this issue, the support for issues with *nix based stuff in my experience here is about 100 fold better than windows support. That is the stuff that makes me very happy that I made the switch almost 2 years ago.

---

### Post by Haagimus on 2010-06-12
how do i mark this topic as closed? i have recovered all my files and it was just a random bad sector development on the HDD

---

### Post by lavinog on 2010-06-12
click on Thread Tools and mark thread as solved.

---

