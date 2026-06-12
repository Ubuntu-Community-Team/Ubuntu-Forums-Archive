---
title: "Why cant I copy a large 30gig image file?"
date: 2010-01-03
forum: General Help
---

### Post by ttallos on 2010-01-03
I have some large image files that are 30 gig and more. I am running Ubuntu 9.10 whenever I try to copy one of these files to another drive I get a error saying the file is too large. I am trying to copy from an external Hard Drive or a slave drive does the same thing. I have a friend who has expressed the same issue. This must be a widespread bug.

---

### Post by NFblaze on 2010-01-03
What's the file system type of the destination locations.

---

### Post by ttallos on 2010-01-03
A RAID 1 MIRROR Array 1Terabyte EXT3/EXT4 is the destination on the ubuntu server The ububtu 9.10 is loaded on an 80Gig or something. Then any drive I am going to slave will always be NTFS and the source drive. I am trying to copy dd images that typically are 20gb-30gb Thanks for any advice you can give.

---

### Post by SuperSonic4 on 2010-01-03
He meant what filesystem is your destination?

If it's fat32 prepare to be disappointed/reformat

---

### Post by amauk on 2010-01-03
> **ttallos said:**
> it is a RAID 1 MIRROR Arrayhe meant filesystem

eg. FAT32, NTFS, EXT2/3/4, etc.

---

### Post by ttallos on 2010-01-03
A ubuntu 9.10 RAID 1 Mirror array is the destination. OK I have an ubuntu machine for years in the basement. ubuntu is loaded on an 80G hard drive then I have a 1T Mirrored array that I have a shared folder to put all my files and stuff in. Sometimes I will slave in a drive that is NTFS with large image files to copy to the array. The array is a mirror RAID 1 EXT3/EXT4. Also I use network connection on smaller files and mostlly have no problem.

---

### Post by amauk on 2010-01-03
you still haven't told us what filesystem is on your 1TB raid array

See here for the filesize limits for various filesystems
[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

---

### Post by ttallos on 2010-01-03
> **amauk said:**
> you still haven't told us what filesystem is on your 1tb raid array

see here for the filesize limits for various filesystems
[http://en.wikipedia.org/wiki/comparison_of_file_systems#limits](http://en.wikipedia.org/wiki/comparison_of_file_systems#limits)

ext3/ext4 RAID 1 Mirror

---

### Post by amauk on 2010-01-03
The EXT's are not a good choice for large files
They are designed for "conventional" filesystem usage

Default max filesize for EXT's is 16GB
You can increase this by specifying larger block sizes (this is somewhat architecture dependant)
but if you need this you're better off using a different filesystem

XFS is probably your best bet for the sizes you're quoting
(XFS was designed to store large amounts of large files - media archives, etc.)
[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

---

### Post by Dayofswords on 2010-01-03
what the heck is on that 30gb image? hi res of all of united states?!

---

### Post by amauk on 2010-01-03
> **Dayofswords said:**
> what the heck is on that 30gb image? hi res of all of united states?!or a 2 hour, 720p animated gif :P

---

### Post by running_rabbit07 on 2010-01-03
Or a VBox drive .vdi file.

---

### Post by Slim Odds on 2010-01-03
> **amauk said:**
> The EXT's are not a good choice for large files
They are designed for "conventional" filesystem usage

Default max filesize for EXT's is 16GB
You can increase this by specifying larger block sizes (this is somewhat architecture dependant)
but if you need this you're better off using a different filesystem

There is nothing wrong with using ext for large files.

The default block size these days is not usually 1K which would give the 16GiB file size limit.

My /home partition defaulted to 4K block size, so I have a 2TiB file size limit.

---

### Post by ttallos on 2010-01-03
Thanks for all the information and replies. Those images are dd images of other machines sometimes I may have a dd image of 250gb-500gb. For now my average dd image is 20GB-30GB

---

### Post by Slim Odds on 2010-01-03
What are you imaging? 

You might want to try clonezilla

---

### Post by dcstar on 2010-01-03
> **amauk said:**
> The EXT's are not a good choice for large files
They are designed for "conventional" filesystem usage
..........
XFS is probably your best bet for the sizes you're quoting
(XFS was designed to store large amounts of large files - media archives, etc.)
[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

Yep, use another FS that can handle that requirement (XFS, Reiserfs):

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

---

### Post by Slim Odds on 2010-01-04
> **dcstar said:**
> Yep, use another FS that can handle that requirement (XFS, Reiserfs):

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

As was mentioned in a previous post, there is nothing wrong with using ext (2,3 or 4).

> **Slim Odds said:**
> There is nothing wrong with using ext for large files.

The default block size these days is not usually 1K which would give the 16GiB file size limit.

My /home partition defaulted to 4K block size, so I have a 2TiB file size limit.

---

### Post by running_rabbit07 on 2010-01-04
> **dcstar said:**
> Yep, use another FS that can handle that requirement (XFS, Reiserfs):

[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

+1 

I haven't been able to find a HowTo yet for setting Ext block sizes.

---

### Post by bodhi.zazen on 2010-01-04
> **running_rabbit07 said:**
> +1 

I haven't been able to find a HowTo yet for setting Ext block sizes.

:lolflag:

man page ?

use the -b flag:

> **-b** *block-size* Specify the size of blocks in bytes. Valid block size vales are 1024, 2048 and 4096 bytes per block. If omitted, **mke2fs** block-size is heuristically determined by the file system size and the expected usage of the filesystem (see the **-T** option). If *block-size* is negative, then **mke2fs** will use heuristics to determine the appropriate block size, with the constraint that the block size will be at least *block-size* bytes. This is useful for certain hardware devices which require that the blocksize be a multiple of 2k. [http://linux.die.net/man/8/mkfs.ext3](http://linux.die.net/man/8/mkfs.ext3)

:twisted:

XFS is nice, BUT, FYI, take care is is relatively unstable with power failure (I know any file system can be corrupted by power failure, but ext3/4 is more robust).

---

### Post by running_rabbit07 on 2010-01-04
[U][Double post.]("http://www.youtube.com/watch?v=XAecD-Arcqg")
[/U]

---

### Post by running_rabbit07 on 2010-01-04
Learn something new every day.

[http://linux.die.net/man/8/mkfs.ext3](http://linux.die.net/man/8/mkfs.ext3)

Bodhi, thanks for the link.

---

### Post by bodhi.zazen on 2010-01-04
> **running_rabbit07 said:**
> Learn something new every day.

[http://linux.die.net/man/8/mkfs.ext3](http://linux.die.net/man/8/mkfs.ext3)

Bodhi, thanks for the link.

You are most welcome.

---

### Post by dcstar on 2010-01-04
> **Slim Odds said:**
> As was mentioned in a previous post, there is nothing wrong with using ext (2,3 or 4).

Yes and no. The various FS types available also perform differently depending on the nature of the application.

As an example, I use reiserfs for my VMware VMs because it deals with the few large files that comprise a VM better than EXTx which seems designed to handle many more smaller files. I basically get better performance because I use a FS that is more optimised to the application I use on it (I have done tests to confirm this).

All FS designs are compromised in one way or another and perform differently depending on the applications they support (which is why so many different ones exist). EXTx is good for general OS use because of its resilience, ability to cope with lots of individual files etc, but it isn't that good for applications that use far fewer large files. It is ok, but you can find better.

---

### Post by Junkieman on 2010-01-07
Just FYI ext3 size limits are [listed here]("http://en.wikipedia.org/wiki/Ext3#Size_limits"), and you can see the current block size of a file system with the [tune2fs command]("http://www.unixtutorial.org/2008/04/default-block-size-in-unix/") :)

You can add xfs support to your system by installing:

```
sudo apt-get install xfsprogs
```

---

### Post by ezsit on 2010-01-07
Why don't you stick with Ext3 instead of using Ext4. Ext4 has a history of problems with large files (anything over 10GB). It may still have problems. Ext3 is just fine.

---

### Post by Junkieman on 2010-01-08
> **ezsit said:**
> Why don't you stick with Ext3 instead of using Ext4. Ext4 has a history of problems with large files (anything over 10GB). It may still have problems. Ext3 is just fine.
The only major issue I knew of (0-byte file write) was a result of badly written apps, only when the PC crashed (power outage) at a very specific time. A [patch has been release]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781") last year. [Its discussed here.]("http://ubuntuforums.org/showthread.php?t=1040199")

---

