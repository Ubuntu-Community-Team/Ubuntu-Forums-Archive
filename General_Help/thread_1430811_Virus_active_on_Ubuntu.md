---
title: "Virus active on Ubuntu???"
date: 2010-03-15
forum: General Help
---

### Post by arashiko28 on 2010-03-15
Today I went to a print center and for no suprise my flasdrive ended filled with viruses but :o they don't go as easy as deleting and then the .Trash_1000 folder. It's the kind of virus that copies the folders names and add a .exe ie: Documents > Documents.exe and they look as a wine executable file. How I can stop this before it spreads through my whole pc?

Keep in mind I do not have windows installed, only ubuntu 9.10.

---

### Post by Chronon on 2010-03-15
You're saying that the file tree on your PC's HD is being corrupted by this?
I would shut down immediately, disconnect my HD and then boot from a LiveCD to have a closer look.

Did you run one of these .exe files?  I'm at a loss for how the malware even started executing.

---

### Post by lisati on 2010-03-15
If it's an .exe file, it's unlikely to hurt your Ubuntu system beyond whatever mischief it can get up to through Wine. 

Be sure to disable Wine's access to "/" if none of your programs actually need it. On my copy (I'm runnint 9.04) I would click on Applications->Wine->Configure Wine, then the "drives" tab, the "Z:" icon (which on my machine is associated with "/") and then click on the "remove" button

---

### Post by arashiko28 on 2010-03-15
I have been scanning with clamav but so far everything seems clean, though I already managed to delete it from the drive, I got pretty nervous about it.

---

### Post by Chronon on 2010-03-15
Your original description was not at all clear.  Where were the renamed folders appearing?  Is it possible that what you were seeing was a result of file system corruption rather than malware?

---

### Post by arashiko28 on 2010-03-15
> **Chronon said:**
> Your original description was not at all clear.  Where were the renamed folders appearing?  Is it possible that what you were seeing was a result of file system corruption rather than malware?

I have checked and re-cheked, no files have been corrupted, it was all on my flash drive, what was shown was a random copy of the folders on my flash drive, showing a wine executable icon, and adding .exe at the name, example, I had a documents folder, and appeared a documents.exe, this was giving me the problems to delete, even with sudo rm -rf through terminal.

So far, seems to be alright now, I have deleted all the files and the .Trash_1000 folder and have unplugged and then back in and keeps clean, even after restart.

---

### Post by asmoore82 on 2010-03-15
> **Chronon said:**
> Your original description was not at all clear.[SIZE="3"]+1[/SIZE]

[quote=arashiko28]Today I went to a print center and ... my flasdrive ended filled with viruses
...
I have checked and re-cheked, no files have been corrupted, it was all on my flash drive[/quote]
In other words, the thread title is a bit of a stretch.

---

### Post by stoneage on 2010-03-15
A Windows computer was responsible for putting them on your flashdrive, they won't be able to run on Ubuntu, except through Wine. Basically you are safe.......

---

### Post by arashiko28 on 2010-03-15
> **stoneage said:**
> A Windows computer was responsible for putting them on your flashdrive, they won't be able to run on Ubuntu, except through Wine. Basically you are safe.......

That part I was clear on it, what made me start the thread was that when I first tried to delete them as I usually do, this time it was a bit harder and then kept appearing, but now everything seems to go back normal.

---

### Post by Chronon on 2010-03-15
> **arashiko28 said:**
> I have checked and re-cheked, no files have been corrupted, it was all on my flash drive, what was shown was a random copy of the folders on my flash drive, showing a wine executable icon, and adding .exe at the name, example, I had a documents folder, and appeared a documents.exe, this was giving me the problems to delete, even with sudo rm -rf through terminal.

So far, seems to be alright now, I have deleted all the files and the .Trash_1000 folder and have unplugged and then back in and keeps clean, even after restart.

Your original post made it sound like the .exes were proliferating while your flash drive was mounted in your linux box (something I [and others] have a hard time accepting).  

If you were having a hard time deleting files then I would suggest checking the file system on the flash drive (i.e. fsck.vfat or similar).

---

### Post by arashiko28 on 2010-03-15
> **Chronon said:**
> Your original post made it sound like the .exes were proliferating while your flash drive was mounted in your linux box (something I [and others] have a hard time accepting).  

If you were having a hard time deleting files then I would suggest checking the file system on the flash drive (i.e. fsck.vfat or similar).

Trust me, it was hard to believe for me too, I have never had this happening before. They were proliferating on my flash drive while on linux. That's why I started the thread. Even my flash drive changed to one looking like a piece of paper, now looks just like usual.

---

### Post by Chronon on 2010-03-15
> **arashiko28 said:**
> Trust me, it was hard to believe for me too, I have never had this happening before. They were proliferating on my flash drive while on linux. That's why I started the thread. Even my flash drive changed to one looking like a piece of paper, now looks just like usual.

Did you run a fsck on that drive?

---

### Post by arashiko28 on 2010-03-15
> **Chronon said:**
> Did you run a fsck on that drive?

what was that???

> /media/KINGSTON$ fsck
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? cancelled!

check aborted.

---

### Post by dcstar on 2010-03-15
> **arashiko28 said:**
> what was that???

You do **not** run fsck on mounted drives.

---

### Post by arashiko28 on 2010-03-15
> **dcstar said:**
> You do **not** run fsck on mounted drives.

How I am supposed to do it, if I cannot see the drive unmounted? I only see cdrom0 and cdrom. Luckily I cancelled.

---

### Post by dcstar on 2010-03-15
> **arashiko28 said:**
> How I am supposed to do it, if I cannot see the drive unmounted? I only see cdrom0 and cdrom. Luckily I cancelled.

You run fsck on the device partition name after it has been unmounted - as 99.999% of other people do.

```
man fsck
```

---

### Post by arashiko28 on 2010-03-15
> **dcstar said:**
> You run fsck on the device partition name after it has been unmounted - as 99.999% of other people do.

```
man fsck
```

Sorry to bother you, I know that part, only that I don't see it if it's not mounted, not graphically nor on terminal, the only way I can still see it is through disk utility, not so useful for what I need.

---

### Post by srs5694 on 2010-03-15
A few thoughts:

First, icon changes sometimes don't show up immediately in a file manager because the file manager may look into the files to determine what they are, and this can take time, especially on a flash drive. I don't know what file manager arashiko28 is using, and in all honesty I don't use them much myself, so I don't know precisely how the file managers in GNOME, KDE, Xfce, and so on do this, but this sort of behavior at least *could* account for some of the reported symptoms (file icons changing on the flash drive after it's been mounted).

It's just this side of conceivable that malware in something other than an executable program file could affect Linux. I've heard of viruses based on Macromedia Flash, for instance. (A quick Google turned up [this story](http://news.cnet.com/2100-1023-803829.html) from as far back as 2002!) I honestly don't know if such a virus could infect a Linux system. (I'd hope that any Flash player on a Linux system in 2010 would be immune to an 8-year-old virus, though!) In theory, though, if your system is set to automatically play media on newly-inserted drives, such a virus could infect your Linux system, or at least your own Linux account.

Files being hard to delete could be accounted for by their status, or the status of their parent folders, being set to read-only (in Windows/FAT/NTFS terminology; in Linux we'd say write permission has been removed).

If I suspected a flash drive had been infected with a virus, my first inclination would be to completely wipe the boot sector, create a new partition, and create a new filesystem on it. Of course, if the drive has the only copies of some important files, this might not be a reasonable approach....

---

### Post by srs5694 on 2010-03-15
> **arashiko28 said:**
> Sorry to bother you, I know that part, only that I don't see it if it's not mounted, not graphically nor on terminal, the only way I can still see it is through disk utility, not so useful for what I need.

In Linux, (almost) all hardware is accessed through files in the /dev tree. Hard disks and flash drives are usually /dev/sda, /dev/sdb, /dev/sdc, and so on, although on some systems hard disks are /dev/hda, /dev/hdb, and so on. Partitions take numbers after these names, as in /dev/sda1, /dev/sda2, and so on. These device names don't change when you unmount a disk, although they will disappear when you physically unplug a USB device. Thus, if your flash drive has one partition that's /dev/sdb1 and it's mounted at /media/flash, it remains accessible as /dev/sdb1 even when you've unmounted it from /media/flash, so long as you don't physically unplug it. You can then run fsck on it, as in "fsck /dev/sdb1", when it's unmounted.

---

### Post by arashiko28 on 2010-03-15
I did thought about it too, but since I have connected it many times over and seems perfect and normal, all I'll do is avoid that place where it got infected and if I ever have to go back, to take a less valuable and empty drive ;) Lesson learned on that side.

On the other side, when I saw all the copies some of them were deleted easily, but a couple weren't so I used terminal, got into the drive and tried to do it using rm -rf and got a permission denial, that's when I freaked out, unplugged the drive and ran a full scan of the computer.

I have been using both for a couple of hours and everything seems back to normal, no corrupted files, no changing icons, no new item that I didn't placed in the drive, so I might say it's solved. 

What does intrigues me is the problems I had to do it, it has never happened to me and literally being the only one in miles around to use Linux, I'm used to get my drive infected every time I have to pass some large files to a windows box.

---

### Post by arashiko28 on 2010-03-15
> **srs5694 said:**
> In Linux, (almost) all hardware is accessed through files in the /dev tree. Hard disks and flash drives are usually /dev/sda, /dev/sdb, /dev/sdc, and so on, although on some systems hard disks are /dev/hda, /dev/hdb, and so on. Partitions take numbers after these names, as in /dev/sda1, /dev/sda2, and so on. These device names don't change when you unmount a disk, although they will disappear when you physically unplug a USB device. Thus, if your flash drive has one partition that's /dev/sdb1 and it's mounted at /media/flash, it remains accessible as /dev/sdb1 even when you've unmounted it from /media/flash, so long as you don't physically unplug it. You can then run fsck on it, as in "fsck /dev/sdb1", when it's unmounted.

Thanks, it has been so long since I last used that, that I completely forgot about it, as soon as I can I'll run it.

---

### Post by arashiko28 on 2010-03-16
This is what got from running fsck:

> fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /deb/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


What do I do from now on?

---

### Post by srs5694 on 2010-03-16
It appears that the disk isn't an ext2 disk -- not surprising, since you said you used it at a public copy shop. It's probably a FAT or NTFS disk. If it's FAT, then using fsck.vfat (if it's installed on your system) might work. For NTFS, there's fsck.ntfs -- but this program just does a few basic checks and then flags the filesystem for more thorough checking by Microsoft's CHKDSK the next time the disk is used in Windows. I wouldn't use it in your situation.

---

### Post by arashiko28 on 2010-03-17
> **srs5694 said:**
>  I wouldn't use it in your situation.

What do you mean with that? Not to use my flash drive?

---

### Post by srs5694 on 2010-03-17
> **arashiko28 said:**
> [quote=srs5694]I wouldn't use it in your situation.What do you mean with that? Not to use my flash drive?[/QUOTE]

No, fsck.ntfs. Sorry about the ambiguity.

---

### Post by arashiko28 on 2010-03-18
No problem, the flash drive is working fine. So, with no further harm done that the initial fuss, I'm going to mark it as solved.
Thanks to all of you who helped!
Arashiko28:D

---

