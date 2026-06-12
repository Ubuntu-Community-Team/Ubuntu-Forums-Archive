---
title: "What's special about the Ubuntu disk manager?"
date: 2011-04-04
forum: General Help
---

### Post by Spirrwell on 2011-04-04
Note: This isn't urgent, but just curiosity, so people don't waste their time if they don't want to.

I've spent an hour trying to format some micro SD card, (through Windows) and it wouldn't format, yet I had no problem formatting other things with the same reader. I felt like I was pretty much out of options and I thought that the card was damaged, but I went into Ubuntu disk manager and format with no problem. I just want to know, what the hell is actually in the disk manager. Technically it doesn't make sense that it would format just fine with Ubuntu and not with Windows, even though I've formatted it with Windows before. I just don't get how it worked... I want to know the programming behind, what's different with the Ubuntu disk manager than Windows' format utility?

---

### Post by Jouke74 on 2011-04-04
- Can you read it now with Windows?

- Both were formatted with the same file system?

- Maybe Ubuntu placed the boot-sector on a new part of the disk. Windows tends to overwrite the old one. 

- Ubuntu put the partition on the end of the disk instead of the beginning?

- Ubuntu kept the first 5% of the space free (EXT3 file system)

Anyway, still I would be careful with putting important data on it...

---

### Post by garvinrick4 on 2011-04-04
I do not own a sd card nor camera just download my kids cards to my machine.
What format are they in?
Are all cards formatted the same?
Could it be just fat?

---

### Post by Spirrwell on 2011-04-04
> **Jouke74 said:**
> - Can you read it now with Windows?

- Both were formatted with the same file system?

- Maybe Ubuntu placed the boot-sector on a new part of the disk. Windows tends to overwrite the old one. 

- Ubuntu put the partition on the end of the disk instead of the beginning?

- Ubuntu kept the first 5% of the space free (EXT3 file system)

Anyway, still I would be careful with putting important data on it...



I formatted it with the EXT file system first, but then I formatted it for FAT32, it works in Ubuntu and Windows. That was my goal, I was trying to get a Windows game from OS to the other, but it was in an incompatible ISO format, so I was using the micro SD as a DVD replacement, I was just wondering why it would work in Linux, Ubuntu in this case, and not Windows, it's been my understanding that Windows doesn't have the ability to zero out sectors, does Ubuntu have that ability with it's disk manager? That's the only logical reason I can see for it... I'm just curious.

---

### Post by garvinrick4 on 2011-04-04
##Homepage on bottom:
```
Package: gnome-disk-utility              
State: installed
Automatically installed: no
Version: 2.32.1-0ubuntu4
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,659 k
Depends: libc6 (>= 2.2.5), libgdu-gtk0 (>= 2.29.90), libgdu0 (>= 2.29.90),
         libglib2.0-0 (>= 2.22.0), libgtk2.0-0 (>= 2.20.0),
         liblaunchpad-integration1 (>= 0.1.17), libnautilus-extension1 (>=
         2.30), libnotify4 (>= 0.7.0), libunique-1.0-0 (>= 1.0.0)
Description: manage and configure disk drives and media
 palimpsest (from the gnome-disk-utility project) is a tool to manage disk
 drives and media: 
 
 * Format and partition drives. 
 * Mount and unmount partitions. 
 * Query S.M.A.R.T. attributes. 
   
 It utilizes udisks.
```
Homepage: [http://git.gnome.org/cgit/gnome-disk-utility/](http://git.gnome.org/cgit/gnome-disk-utility/)

---

### Post by garvinrick4 on 2011-04-04
Windows does not read ext format where linux reads ext,NTFS,fat ect. ect. ect.
Most users I believe use gparted to format and partition in Ubuntu.

---

### Post by Spirrwell on 2011-04-04
I said that I formatted to EXT then I formatted it to FAT32 with Ubuntu, it works with both Ubuntu and Windows, but that's not what I'm asking, I'm asking why it would work now since I formatted it with Ubuntu, and not when I tried to format it with Windows.

---

### Post by matt-fender on 2011-04-04
> **Spirrwell said:**
> I said that I formatted to EXT then I formatted it to FAT32 with Ubuntu, it works with both Ubuntu and Windows, but that's not what I'm asking, I'm asking why it would work now since I formatted it with Ubuntu, and not when I tried to format it with Windows.


This has happened to me countless times with many different types of Media. Still haven't worked out why it happens.. Just be glad you had a Linux OS to hand:lolflag::guitar:

---

### Post by Jouke74 on 2011-04-04
If it was still EXT when you tried to format it with Windows, then it's easy: Windows can't read Ext without any special tricks so it won't find any "good disk" meaning readable (boot) sectors to start formatting on it. It will report that it is not able to format the disk.

The other option is indeed that Ubuntu skipped a bad sector that Windows required to be ok (meaning most likely the FAT table and boot sectors).

I suspect the first.

---

### Post by garvinrick4 on 2011-04-04
> **Spirrwell said:**
> I said that I formatted to EXT then I formatted it to FAT32 with Ubuntu, it works with both Ubuntu and Windows, but that's not what I'm asking, I'm asking why it would work now since I formatted it with Ubuntu, and not when I tried to format it with Windows. Wow a bit snippy there, must be a youngster Huh. Enjoy you Linux partner.

---

