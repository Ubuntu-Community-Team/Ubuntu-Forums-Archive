---
title: "hard drive is a mess"
date: 2012-01-20
forum: General Help
---

### Post by mblack3nd on 2012-01-20
OK...I have been working with this issue for a while. A couple of weeks ago, I decided to go ahead and do a clean re-install of Linux. To accomplish this task, I was resizing my NTFS partition that contained all my files and of course, the computer froze up and came back to a messed up partition. After running testdisk on it and trying a number of options, I hooked up the HDD to a computer operating Windows to run the whole chkdsk f/ fella on it, as gparted said to do. It got the partition somewhat working again. After two tries, it completed it all the way through. That got the partition somewhat working again; I was able to see most of the various folders and what not but here is the issue I haven't been able to fix.

Some of the directories I can't even open and more importantly, there are a number of files that appear to be corrupt in some way. For example, in a group of pdfs, some I can open and some cannot. Same with jpgs and whatnot. The error for a jpg, i.e., is "Could not open xxx.jpg; Error interpreting JPEG image file (Not a JPEG file: starts with 0x56 0xfa)"

Any idea what I can do from hear that might allow me to salvage this partition yet (or at least the files)? I have a buddies external now with enough space to dump a foremost search into it or whatever but foremost can give back filenames (or at least is hasn't) and that is a pain to deal with 1000s of files. 

Thanks and lets see what advice y'all have. Thanks in advance!

---

### Post by xyzzyman on 2012-01-20
Haven't used foremost but assuming it's alot like photorec which finds jpeg's, pdf's, etc... Unfortunately this is what you'll have to do. chkdsk restored the 'index' of the drive, but unfortunately files had already been moved so they aren't where the index thinks they are. There are some commercial recovery programs that will identify old copies of allocation tables and I've had luck on NTFS volumes (It gave me over 200 different ones to choose from, most crap though), but they are pricey. I already had recovered everything via photorec but had the same problem of no file names. 

It was my fault as I hadn't done a backup recently and was resizing and after 3 hours saw it had finished the 'test' resize and was starting to real one so I cancelled being an idiot after being up over 24 hours and sick and BAM. 200gigs gone.

The thing is DO NOT USE THE DRIVE. Especially running any OS installed on that partition, especially if it's Vista or Win7 as they do automatic defragging in the background and will move corrupt files around instead of leaving them as is and then that data is definitely gone bye-bye.

---

### Post by mblack3nd on 2012-01-20
Alrighty...I have written a few items to it that I had on my phone to replace the 'corrupt' jpegs...

anyone else have any thoughts...I also might be willing to use one of those recoveries you mentioned if it came down to that

---

### Post by mblack3nd on 2012-01-24
gonna give this a bump...

i wanted to see if you or anybody here might have an idea of how to go about fixing the drive (more than likely using a DR pro) and what exactly I need to have done to the drive so that I know what I am talking about (to some extent) when I take it in to someone if that is what I have to do.

---

### Post by Dngrsone on 2012-01-24
Clone the drive and leave the original alone, then do your recovery work on the cloned drive.

Have you figured out yet that this is why everyone nags you to back up your stuff before doing anything that might prove catastrophic?

---

### Post by mblack3nd on 2012-01-24
Yes...I have a clone but not sure what to do here besides running foremost/photorec and still getting nowhere...

I also did not too long ago back it up but my backup drive now has bad heads and will cost a pretty penny to fix that drive or recover data or whatever so I figure this might be cheaper to fix if I need to send it off to someone since I assume they won't have to open it up.

---

### Post by oldfred on 2012-01-24
If checkdisk recovered data, do you have files in the new chkdsk folders it creates?

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by mblack3nd on 2012-01-24
I did not realize that chkdsk (on windows) created a copy of all the files it was working with.

Testdisk, photorec, and foremost all carve things out but it still does not help as it produces a vast number of trash files and they do not have names which makes recovering files virtually impossible via those methods

---

### Post by oldfred on 2012-01-24
It is not impossible but yes it is difficult to recover files as it only recovers extensions.

You can easily recover photos and music as the important info is in the file and can be used to rename the file. I was recovering text files (and now save file name in text files). So I had to do a lot of grep to find identical versions of file and diff to see which was the newer.

Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

