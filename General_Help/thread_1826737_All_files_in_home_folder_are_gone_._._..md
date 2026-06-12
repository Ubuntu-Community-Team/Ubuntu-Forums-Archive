---
title: "All files in home folder are gone . . ."
date: 2011-08-17
forum: General Help
---

### Post by rabbit_fighter on 2011-08-17
. . . except mp3s?

I don't know what just happened, but all my photos are gone, as are just about all the other files in my home directory.  The file structures are there (all the folders and subfolders under /home/matt/pictures), but there are no files in any of them.

Scattered around the home folder, there are folders that still have stuff in them, but lots are empty.  Pictures are by far the most precious thing gone.

I was playing around in a Virtualbox install of PC Linux and trying to get my home folder to display there.  Did I do something bad? (I was granting read/write).

Any tips on how I might recover?  Nothing in trash.  I have a backup that is fairly recent, but I'm afraid I might lose some precious stuff.

:(

btw - this is Ubuntu 10.10 - NOT KUBUNTU

---

### Post by rabbit_fighter on 2011-08-20
No advice?

Anybody got advice regarding forensic tools to maybe recover some of the jpg files I lost?

---

### Post by coffeecat on 2011-08-20
> **rabbit_fighter said:**
> No advice?

I'm really surprised that no on posted any help for you. Better late than never...

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Have a read of that link. Scroll past testdisk - that is for recovering partitions, not files. Go down to photorec - that's the tool you need for recovering lost files. But you need to install testdisk to get photorec.

Use a live CD, not your hard drive install of Ubuntu, because the more you use the hard drive, the more deleted files are likely to be overwritten and the deleted files are in your /home. And use an external drive to copy the recovered files to. I've seen at least one person attempt to copy recovered files back to the partition from which they were recovering deleted files - bad idea!

The recovered jpegs will not have the original filenames - you will get seemingly arbitrary filenames for everything - but if the lost jpegs have exif metadata you should be able to rename them back to something meaningful from that.

Be aware also that photorec will search for and recover many types of files:

>  PhotoRec is file data recovery software designed to recover
 lost pictures from digital camera memory or even Hard Disks.
 It has been extended to search also for non audio/video headers.
 It searchs for following files and is able to undelete them :
 * Sun/NeXT audio data (.au)
 * RIFF audio/video (.avi/.wav)
 * BMP bitmap (.bmp)
 * bzip2 compressed data (.bz2)
 * Source code written in C (.c)
 * Canon Raw picture (.crw)
 * Canon catalog (.ctg)
 * FAT subdirectory
 * Microsoft Office Document (.doc)
 * Nikon dsc (.dsc)
 * HTML page (.html)
 * JPEG picture (.jpg)
 * MOV video (.mov)
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
 * Moving Picture Experts Group video (.mpg)
 * Minolta Raw picture (.mrw)
 * Olympus Raw Format picture (.orf)
 * Portable Document Format (.pdf)
 * Perl script (.pl)
 * Portable Network Graphics (.png)
 * Raw Fujifilm picture (.raf)
 * Contax picture (.raw)
 * Rollei picture (.rdc)
 * Rich Text Format (.rtf)
 * Shell script (.sh)
 * Tar archive (.tar )
 * Tag Image File Format (.tiff)
 * Microsoft ASF (.wma)
 * Sigma/Foveon X3 raw picture (.x3f)
 * zip archive (.zip)

You will get thousands of files recovered so make sure your backup medium is large enough and be prepared for a major sorting exercise when all is done.

Good luck with that.

**EDIT**: by the way, when you've finished recovering what you can, buy yourself a (or two) external hard drive(s), and back all your personal data up. And then back them up again. Your personal data is worth more than the cost of the physical media on which it is stored.

---

