---
title: "Graphical view of used hard disk sectors"
date: 2011-03-05
forum: General Help
---

### Post by Socob on 2011-03-05
Hello everyone,

I'm looking for something very specific in a program, but so far, I haven't been able to find anything. Basically, I need a program that displays which sectors on a hard disk are used, so it should show the physical position of the data on the drive (specifically, on an NTFS partition of a disk) - I guess it would need to look at the Master File Table. If anyone remembers that, I'm pretty much looking for what the built-in Disk Defragmentation program did on Windows XP, except that I only care about the graphical representation of the disk. I guess a command-line/text-only program would be okay as well, if it somehow managed to convey the same information with text.

So far, the only things I've found are programs like the GNOME Disk Usage Analyzer or fdisk for the command line, but what those do is show how much space is used. What I would like to know is *where* it's used. So, if anyone knows a program like that, I'd appreciate your help.

---

### Post by turtle153 on 2011-03-05
Sounds like you need [GParted.]("apt:gparted") It has a graphical representation of the partitions at the top so you can see where they are on the drive.

---

### Post by coffeecat on 2011-03-05
That's an interesting question. The only thing that comes near that I have been able to find is the terminal command 'ntfsls'. It's part of the ntfsprogs package. Using the options -liR *might* get you what you want although how you'd interpret that mass of output is beyond me. It's certainly not graphical.

Why did you want to do this? I would have thought it would only be of use on a Microsoft filesystem in which case you would be better off using a Windows app. One of the many available defragmenters would have the graphical representation you want.

> **turtle153 said:**
> Sounds like you need [GParted.]("apt:gparted") It has a graphical representation of the partitions at the top so you can see where they are on the drive.

Have a look at the OP's post again. This will not solve the OP's question.

---

### Post by Socob on 2011-03-05
> **coffeecat said:**
> That's an interesting question. The only thing that comes near that I have been able to find is the terminal command 'ntfsls'. It's part of the ntfsprogs package. Using the options -liR *might* get you what you want although how you'd interpret that mass of output is beyond me. It's certainly not graphical.
Uh, yeah. Reading all that isn't really possible (I'd have to look up what the individual columns mean, too), which is the main reason why I was looking for a graphical program - I just don't see how you'd be able to do that just with text.

> **coffeecat said:**
> Why did you want to do this? I would have thought it would only be of use on a Microsoft filesystem in which case you would be better off using a Windows app. One of the many available defragmenters would have the graphical representation you want.
Huh, I didn't know there were so many defragmenters out there besides the standard Windows one (which doesn't have the graphics anymore since XP), so I didn't really think of that. What I actually wanted to use it for was backing up the data of a disk, and since just copying the files is generally not the best idea, especially if you're copying to FAT/FAT32, I wanted to put it into an image file. The thing is, the disk was huge (500GB), but there was only about 15GB data on there, total, half of which was on some other end of the disk than the rest for some reason. Because backup discs/programs like Clonezilla (which uses partclone) go through the whole drive, which takes ages (at least 10 hours, as it looks like), I thought I'd just use dd to copy the areas I need, but for that, I'd have to know where they actually are.

So that was the long story. It just turned out that I might not even need an exact clone, so I could probably just copy the files after all. Still, now I'm curious if something like this actually exists for Linux. I'd actually be surprised if it didn't given the large amount Linux of rescue discs and solutions.  It doesn't look like it'd be hard to do (you'd probably just have to read the MFT), but apparently no-one/few have done it yet.

---

### Post by coffeecat on 2011-03-05
> **Socob said:**
>  and since just copying the files is generally not the best idea, especially if you're copying to FAT/FAT32, I wanted to put it into an image file.

Why isn't simply copying the files a good idea? I've often copied tens of gigabytes of data from NTFS > NTFS, NTFS > FAT32, FAT32 > NTFS, NTFS > ext4 and many other combinations. I've not had a problem.

---

### Post by srs5694 on 2011-03-05
I also recommend copying the files (using cp, rsync, tar, cpio, or whatever other file-level utility you like). This doesn't work well for a Windows boot partition, but in most other cases, it'll do the job fine.

If you do need to preserve NTFS data (ownership, permissions, etc.), then doing the file copying from Windows makes sense. I've use the [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) package with good success from Windows, even to back up and restore a Windows boot partition.

The Linux tool that I know of that best preserves low-level NTFS metadata without backing up unused space is ntfsclone, which is in the ntfsprogs package. It backs up NTFS on a sector-by-sector basis, so in principle it should be reasonably fast on a sparsely-used disk. I've successfully backed up and restored Windows systems with ntfsclone; however, if it's a boot disk, you've got to be very careful to create a target partition that starts on the same sector as the original, or else Windows won't boot.

---

### Post by wojox on 2011-03-05
I use [Defraggler]("http://www.piriform.com/defraggler") on my Vista box.

---

### Post by Socob on 2011-03-05
> **coffeecat said:**
> Why isn't simply copying the files a good idea? I've often copied tens of gigabytes of data from NTFS > NTFS, NTFS > FAT32, FAT32 > NTFS, NTFS > ext4 and many other combinations. I've not had a problem.
Well, FAT32 doesn't support NTFS metadata or symbolic links, and there's still that pesky 4GB file size limit. But as I've said, it seems like I'll be getting away with just copying the files.

> The Linux tool that I know of that best preserves low-level NTFS  metadata without backing up unused space is ntfsclone, which is in the  ntfsprogs package. It backs up NTFS on a sector-by-sector basis, so in  principle it should be reasonably fast on a sparsely-used disk. I've  successfully backed up and restored Windows systems with ntfsclone;  however, if it's a boot disk, you've got to be very careful to create a  target partition that starts on the same sector as the original, or else  Windows won't boot.
Hm. Either I messed something up when I tested Clonezilla, or the speed difference when using a USB stick is bigger than I thought. I assumed it was taking a long time because it was still searching through the sectors even if it skipped unused ones, but I guess the slow USB was at fault.

> I use [Defraggler]("http://www.piriform.com/defraggler") on my Vista box. 	
It looks like that does exactly what I wanted. Too bad it doesn't run under Wine, though.

---

