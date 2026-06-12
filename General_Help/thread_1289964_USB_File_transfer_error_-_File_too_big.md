---
title: "USB File transfer error - File too big"
date: 2009-10-13
forum: General Help
---

### Post by jamesey on 2009-10-13
I'm trying to move an 8GB video file from my desktop machine to my external hard drive via USB.

The file is 8 GB
My external HD has over 60GB of free space
My external HD is formatted as FAT 32
My external HD is connected via USB
I can copy 2 GB files to my external hard drive
The file transfer actually starts normally. When it gets to the 4 GB mark I get a pop up error stating "this file is too big"

How do I troubleshoot this?

---

### Post by blackened on 2009-10-13
Wikipedia says:

> The maximum possible size for a file on a FAT32 volume is 4 GB minus 1 byte (232&#8722;1 bytes). Video applications, large databases, and some other software easily exceed this limit. Larger files require another formatting type such as NTFS.

Try formatting the drive using a different filesystem.

---

### Post by TombKing on 2009-10-13
> **jamesey said:**
> I'm trying to move an 8GB video file from GB mark I get a pop up error stating "this file is too big"

How do I troubleshoot this?

You don't.
Use NTFS or some other file system.
From [http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)
"The maximum possible size for a file on a FAT32 volume is 4 GB minus 1 byte (232&#8722;1 bytes). Video applications, large databases, and some other software easily exceed this limit. Larger files require another formatting type such as NTFS."

.....err yeah what he said above me...

---

### Post by easoukenka on 2009-10-13
These recommandations are correct.  Only problem is these filesystems are not as compatible with other operating systems.  Maybe just use rar or some other file splitting tool if you are not doing this too often.

---

### Post by TombKing on 2009-10-13
> **easoukenka said:**
> These recommandations are correct.  Only problem is these filesystems are not as compatible with other operating systems.  Maybe just use rar or some other file splitting tool if you are not doing this too often.


well so far i have had good luck with getting data to and from ntfs when running ubuntu. it actually has made it less of a pain for me when transferring files as it does not give a frack about the ntfs permissions where other windows boxes have fits over the data.

that said it is probably easier to break up the file into smaller bits.

---

### Post by blackened on 2009-10-13
> **easoukenka said:**
> ...these filesystems are not as compatible with other operating systems...

NTFS works just fine in both Windows (obviously) and Ubuntu. The days of incompatability/data corruption are so two years ago.

---

### Post by jamesey on 2009-10-13
Thanks for the information everyone. Any recommendations for a file splitter? 

I need to keep the files as FAT32 so my Phillips DVD player can connect to my external HD via USB.

---

### Post by P4man on 2009-10-13
Use RAR. Install it first:

```
sudo apt-get install rar
```

Then right click the file, compress. Change the type to RAR, and click "other options" where you can split the file in volumes of x Mb.

---

### Post by nikhilbhardwaj on 2009-10-13
you may want to use ffmpeg
if you want the videos to play on your dvd player

---

### Post by zer0x on 2009-10-13
Hi,

I would usually do this with 'split' and 'cat'. If the target machine is running Windows you can use the 'copy' command in a DOS prompt instead of 'cat' to rejoin the files.

To split 'testfile' into 4GB parts:

```
split -b 4GB testfile testfile_part_
```

An 8GB file would result in: testfile_part_aa, testfile_part_ab

To rejoin the files in linux:

```
cat testfile_part_aa testfile_part_ab > testfile
```

To rejoin the files in Windows (cmd.exe):

```
copy /B testfile_part_aa+testfile_part_ab testfile
```

HTH

zer0x

---

### Post by StuartN on 2009-10-13
Is there any convenient way to split a big VOB file so that each chunk is still a valid VOB file? It is so easy now with vobcopy and the like to create a single-VOB movie file, which then doesn't fit on a FAT32 USB stick or play in a DVD machine...

---

### Post by zer0x on 2009-10-13
Hi,

Mencoder can be used to split a video into parts:

```
mencoder -endpos 00:45:00 -oac copy -ovc copy source.avi -o target_pt1.avi

mencoder -ss 00:45:00 -oac copy -ovc copy source.avi -o target_pt2.avi
```

This would split a 90 minute video into two 45 minute parts.

If you need to split into more than two parts don't forget that -endpos is relative to -ss, for example -ss 00:10:00 -endpos 00:30:00 will give you 30 minutes of video (start 00:10:00, end 00:40:00).

HTH

zer0x

---

### Post by StuartN on 2009-10-14
> **zer0x said:**
> This would split a 90 minute video into two 45 minute parts.

But if the source is a valid .VOB (with whatever non-video data is in a .VOB) then this will not output valid .VOB files, will it?

Alternatively, how would you strip a .VOB of all the DVD pgc and other data to make a file suitable for splitting with mencoder?

Edit: Or to put this in a better way, what is the best method for getting stuff off a DVD and onto a USB stick whilst making sure it is widely compatible (i.e. FAT32, nothing bigger than 4 GB and file types that play in a commercial DVD player with a USB socket)?

---

### Post by zer0x on 2009-10-14
I need to look into splitting .VOB files, will get back to you on that!

However, this site has an excellent tool for generating mencoder command-lines for DVD -> XviD encoding, which is supported by the majority of USB capable DVD players.
[URL="http://quadpoint.org/projects/simplerip"]
http://quadpoint.org/projects/simplerip[/URL]

---

