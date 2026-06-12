---
title: "Error: A partition cannot have a length of -1 sectors"
date: 2009-10-23
forum: General Help
---

### Post by watson524 on 2009-10-23
Hi all,

I have a 2tb external drive that was NTFS with nothing on it brought over from a Windows machine that's now /dev/sdc1 on my linux box. I didn't like the disk label on it and used gparted to give it a new one (device, set disk label). I changed it to "2tbext" because I didn't care if it erased anything on it since nothing was there. I don't know if this operation actually took place because I don't see anything in pending operations but it does say the partition is unallocated and the file system is unallocated. So then when I right click and go to new to partition it as NTFS, I want one partition and I get the following error "A partition cannot have a length of -1 sectors". New size is the whole thing, and create as is primary partition. So now I'm not sure what's what.

thanks!:confused:

---

### Post by watson524 on 2009-10-23
I applied some brute force to this and it's working.... no really, I took the entry out of fstab and plugged it in to my windows machine and formatted it with a new drive label and now have it back on my linux box shared. I think I'm having a problem with it mounting autmotically even though it's back in fstab but I have to check that after I move about 70gb of data over.

---

### Post by P4man on 2009-10-23
I saw this on wikipedia:
> 
Because partition tables on master boot record (MBR) disks only support partition sizes up to 2 TiB, dynamic or GPT volumes must be used to create bootable NTFS volumes over 2 TiB.

[http://en.wikipedia.org/wiki/Ntfs](http://en.wikipedia.org/wiki/Ntfs)

Perhaps thats a limitation you're bumping in to?

---

### Post by watson524 on 2009-10-23
Possibly. I'll have to do some more investigating at some point. I was reading the gParted didn't like drives this large and that command line should work but that didn't seem to help either.

---

### Post by T.E.N. on 2009-11-03
> **P4man said:**
> I saw this on wikipedia:
[http://en.wikipedia.org/wiki/Ntfs](http://en.wikipedia.org/wiki/Ntfs)
[2GB max. for MSDOS partition table] Perhaps thats a limitation you're bumping in to?Presumably not. We rather seem to be encountering (ever more often since 1+ TB drives have become commonplace) an issue with GParted that has been around for years (and remains uncorrected at least on the Hardy Heron 8.04 LTS):
[http://gparted-forum.surf4.info/viewtopic.php?id=281](http://gparted-forum.surf4.info/viewtopic.php?id=281)

Creating the partition with cfdisk will do the trick (create whole drive as one primary partition of type 07; don't forget to select "write" before quitting), and GParted should happily format it to NTFS once created by the command-line application that in my experience to this day keeps proving itself to be the most versatile and reliable, ever since the days in another millennium when it had to maintain partitions interoperable with various flavors of Windows and the OS/2 Boot Managers.

sudo apt-get install ntfsprogs (as in [http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29](http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29)) is probably required before being able to mount and write to an NTFS partition (bear in mind that something like /dev/sdd1 rather than /dev/sdd is the one).

---

