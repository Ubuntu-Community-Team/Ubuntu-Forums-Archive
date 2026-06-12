---
title: "USB Startup Disk Creator borked my external drive"
date: 2009-11-20
forum: General Help
---

### Post by gontofe on 2009-11-20
I was trying to create a USB startup disk, and encountered an error, but as a click-happy user, I accidentally selected my external hard drive and then clicked 'format'. 

I've tried to restore the partition table using testdisk, and when I run a quick test and press [p] I can see some of my files...

The problem is that it tries to recognise the entire drive as one large partition, rather than two, and although I've read the documentation [here]("http://www.cgsecurity.org/wiki/Running_TestDisk") I can't understand how to recreate the previous partition table and recover my files! Can anyone please help me?

I am unsure of the exact sizes of the partitions that were present on the drive...

---

### Post by mechro on 2009-11-20
A fuller Testdisk tutorial is here...

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Have you done a "Deeper Search"?

---

### Post by gontofe on 2009-11-21
Yes, I've done a deeper search, and it detects the disk as one large partition rather than two smaller ones (although it does detect the files on the partitition). I've tried saving the partition table  as one large partition, and it won't mount, as it says there's an error with the superblock.

I've also tried running parted to rescue the partition by putting in various combinations of partition size to no avail.

gpart also 'guesses' the partition to be one large partition covering the whole drive.

As the files are still on the drive, is it not possible for a tool to show me a list of all files on the drive, so I can try creating a partition table of roughly the right sizes? How would I do this? testdisk allows you to add partitions, but it asks for this information in cylinder|head|sector format, and I haven't got a clue!

Is there a tool that can display files on a file with a damaged partition table (I have deleted the one testdisk created)? Failing that, if I manage to create one large partition on the drive and get it to mount correctly will my files appear, or is that reliant on recreating the previous structure?

---

### Post by P4man on 2009-11-21
I can feel your pain, I did the exact same thing a while ago, formatting a terrabyte external HD.
you could try photorec, but i did not have much success with it on my attempt. My drive was an NTFS dynamic disk, and I only managed to get most of my data back using this:
[http://www.easeus.com/datarecoverywizardpro/](http://www.easeus.com/datarecoverywizardpro/)
Its for windows and its not free, allthought the demo will show a list of files. The full version.. can be found or bought online.

But perhaps you'll have more luck with photorec than I did..

---

### Post by gontofe on 2009-11-21
Just for info, this is the output of testdisk when it detects one large partition and I hit [p] to list the files it finds. It doesn't seem to detect the entire structure, as this folder was at /My Documents/My Music on the first partition (and of course, the file list should start at the letter a!

How do I get it to find the rest of my files?


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
   * FAT32 LBA                0   1  1 38153  63 32   78139360
Directory /

-rwxr-xr-x     0     0   3316216 17-Nov-2008 11:56 SHANKS~1.MP3
-rwxr-xr-x     0     0   5048320 10-Apr-2009 10:41 Shapeshifters - Lola's Theme
-rwxr-xr-x     0     0   3668064  3-Nov-2008 14:43 Shed Seven  - Disco Down.mp3
-rwxr-xr-x     0     0   5259264 10-Apr-2009 10:41 Shed Seven - Dolphin.mp3
-rwxr-xr-x     0     0   5644707 29-Jul-2007 18:33 Sheryl Crow - My Favorite Mis
-rwxr-xr-x     0     0   7315928 17-Nov-2008 11:56 Sheryl Crow - There Goes the
-rwxr-xr-x     0     0   5316608 15-Feb-2006 15:45 Shirley Bassey  - Where Do I
-rwxr-xr-x     0     0   4293514 15-Feb-2006 15:45 Shola Ama and Moise  - Sympho
-rwxr-xr-x     0     0   3429065 17-Nov-2008 11:56 SiA  - Taken For Granted.mp3
-rwxr-xr-x     0     0   3105336 15-Feb-2006 15:45 Silicone Soul  - Right On! (R
-rwxr-xr-x     0     0   2942191 15-Feb-2006 15:46 Silmarils  - Va y avoir du sp
-rwxr-xr-x     0     0   4644523 19-Mar-2007 18:09 _AD267~1.MP3
-rwxr-xr-x     0     0   3446950 15-Feb-2006 15:46 Sinclair  - Si C'est Bon Comm
-rwxr-xr-x     0     0   3852288 15-Feb-2006 15:46 Singuila  - C'est trop.mp3
-rwxr-xr-x     0     0   5101733 15-Feb-2006 15:46 Sisqo  - The Thong Song.mp3
                                                   Next
Use Right arrow to change directory, c to copy,
    h to hide deleted files, q to quit

---

### Post by mechro on 2009-11-21
Er... probably something you don't want to do, but could you take the drive out of its case and plug it in as an internal drive? I'm just wondering whether it was originally set up to work as a Windows back-up drive and you've never reformatted it since.

---

### Post by gontofe on 2009-11-21
I could do, how would this help me though? I believe I did reformat it in linux as fat32 in order to be able to use it in Windows and Linux...

---

### Post by mechro on 2009-11-21
> **gontofe said:**
> I could do, how would this help me though? I believe I did reformat it in linux as fat32 in order to be able to use it in Windows and Linux...

OK, forget that, it probably won't help.

In Testdisk, instead of **Analyse**, do **Delete**(delete all data in the partition table). Reboot and run Testdisk Analyse again.

---

