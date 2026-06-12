---
title: "NFTS archive partition: xubuntu reads everything, windows is snobbish"
date: 2010-02-25
forum: General Help
---

### Post by Joe Question on 2010-02-25
Hi all,
here's today's problem: I have a dual boot system (windows 7, and xubuntu/ubuntu). 
I also made a 3rd NTFS archive partition so that data on it could be accessible anytime, from any OS I use. 
The partition is perfectly mounted in xubuntu and windows sees it without a problem, too. 
I created it using gparted. Both OS can also write on it. 
The problem comes when reading: if I write a file on the archive NFTS partition from windows, xubuntu will see it. If I write a file on the same partition from Xubuntu, windows will not see it, it will just see the files that he wrote himself on it. 
Any idea why?

BTW my pc is an Acer timeline 1810t running both ubuntu and windows in 64 bit, sata hdd in ahci mode.

---

### Post by gsmanners on 2010-02-25
Seems to be a Windows 7 issue (from looking at similar threads). The consensus workaround seems to be to use an ext2/3/4 formatted drive to share files and use [Ext2Fsd]("http://www.ext2fsd.com/").

---

### Post by Mark Phelps on 2010-02-26
> **gsmanners said:**
> Seems to be a Windows 7 issue (from looking at similar threads). The consensus workaround seems to be to use an ext2/3/4 formatted drive to share files and use [Ext2Fsd]("http://www.ext2fsd.com/").

There must be some other problem at work here.  I use NTFS partitions to share data between different Linux distros and different MS Windows OSs -- and have (in several years now), never experienced the problem the OP describes.

---

### Post by Joe Question on 2010-02-26
Thanks for your quick replies... 

I also think there must be some sort of other problem here as many people do share data on a ntfs partition without a problem. 

It could be a windows problem in reading as well as ubuntu's in writing to the windows' standard...  dunno.

I will keep in mind the Ext2 IFS solution as last resource as I had to format so many times and... now that every partition seems to work fine I am afraid to touch it again.

---

### Post by Mark Phelps on 2010-02-26
I really doubt its strictly a Win7 problem as I do this kind of stuff every day, have done that for months, and have never encountered a problem like this.

If you're mounting the shared NTFS partition in Ubuntu, make sure that you're specifying ntfs-3g as the filesystem, not ntfs.

There's an offhand chance that Ubuntu is buffering the NTFS writes, and when you shutdown Ubuntu, those buffered writes are still pending.

So, before you logout or shutdown Ubuntu, when the NTFS shared drive is mounted, see about manually "safely removing" the mounted partition.  You can do that by right-clicking the drive icon on the desktop and choosing safe removal.

---

### Post by SecretCode on 2010-02-26
I've had no such problems with internal ntfs partitions mounted via fstab, but definitely with partitions mounted after booting you need to 'safely remove' or this can happen.

Even once you've got it working, you may have ntfs errors. Run _chkdsk driveletter: /f_ in windows.

---

### Post by gsmanners on 2010-02-26
It goes without saying that unless you properly unmount a drive, it will not save its state properly, and you will lose files. That's true even for non-NTFS systems.

---

### Post by SecretCode on 2010-02-27
But it's reasonable to expect that an orderly shutdown **would **unmount drives correctly, and automatically. In my experience it's safer to unmount ntfs drives manually before shutting down.

---

### Post by Joe Question on 2010-02-27
> **Mark Phelps said:**
> 

There's an offhand chance that Ubuntu is buffering the NTFS writes, and when you shutdown Ubuntu, those buffered writes are still pending.

So, before you logout or shutdown Ubuntu, when the NTFS shared drive is mounted, see about manually "safely removing" the mounted partition.  You can do that by right-clicking the drive icon on the desktop and choosing safe removal.


:) Solved. Again, thanks to the community for the support.
This is what happened: I have both Xubuntu + Ubuntu on my system. 

When I tested the NTFS archive partition on ubuntu I remember it didn't shut properly, so that explains why the files stored on "NTFS Archive" were not there anymore once in windows .
I tested it several time now and when ubuntu shuts down properly, everything works perfectly. 

In Xubuntu though, it wouldn't. 

The reason is that I had created a shortcut icon on the desktop to my "NTFS Archive" partition and used that to store files (which seemed to be there at the moment but wouldn't be visible later from windows). 
Now I know that in order to get things right, I must add files from the "real" path, i.e. "filesystem-media-NFTS Archive". 
 
Is there a way to create a working shortcut to the desktop? Xubuntu, differently from Ubuntu doesn't show an icon for all mounted partitions on the desktop.

Anyway, big thanks to everyone :)

---

