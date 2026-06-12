---
title: "crap! lost NTFS partition with photos!"
date: 2009-09-25
forum: General Help
---

### Post by Roclemir on 2009-09-25
Ok, deal is, i have a 1TB external hard drive. Last weekend i picked me up a shiny new pc that i wanted to run as a home server. Idea was, i'd mount the 1TB to like /data1 or something on installation of the server, which worked well, except dumbass me didn't backup the files on it first. I had heaps of movies, music, but what's really important is all the photos on there. There's like 6 years of photos. 
 
Was really* really*  stupid of me not to back em up. 
 
Anyways, server works fine , with a shiny BLANK 1TB hdd with a ext3 fs. I've poured over the internet looking for solutions. I foudn a windows program that finds all the files i want however, after finding the files it wants $100USD outta me! typical windows app. I found this nifty little linux distro called Trinity Rescue kit, but it only seems to want to play with existing partitions, and since the existing partition is ext3, it doesn't recognise the old partition.
some please help me. My wife is gonna kill me. 
 
p.s. I've only been playing with linux for a couple of months now (and i've only played with ubuntu distros), so please be patient and talk to me like i'm a baby, hopefully i'll understand.
 
Thanks

---

### Post by Roclemir on 2009-09-25
BTW: When trying to use ntfsundelete with the trinity distro, i get error message 
 
Failed to startuop volume: invalid argument
Failed to mount '/dev/sdb1': invalid argument
The device /dev/sdb doesn't have a valid NTFS 
 
I'm thinking this is due to it currently being ext3

---

### Post by abaden on 2009-09-25
You're going to need to shell out for some recovery software. And it's going to take awhile. 

First, turn off the machine, and leave the drive alone. The less you touch the new partition, the better. Second, you're going to need some recovery software. Since it's NTFS, [O&O]("http://www.oo-software.com/home/en/") might be your best bet. I use O&O myself and it works great. But be prepared to do a bit of work, and next time, make backups! The specific O&O product you want is probably FormatRecovery. 

Sorry for the bad news. :( The good news is that O&O will probably be able to recover everything, unless you did a super thorough job formatting. 

Let us know how it goes. And good luck!


Alex

---

### Post by abaden on 2009-09-25
> **Roclemir said:**
> BTW: When trying to use ntfsundelete with the trinity distro, i get error message 
 
Failed to startuop volume: invalid argument
Failed to mount '/dev/sdb1': invalid argument
The device /dev/sdb doesn't have a valid NTFS 
 
I'm thinking this is due to it currently being ext3

Unfortunately NTFS undelete is for undeleting files from a partition, not recovering an entire partition. :(


Alex

---

### Post by earthpigg on 2009-09-25
> **abaden said:**
> You're going to need to shell out for some recovery software. 


***No.***

> And it's going to take awhile.

Yes, maybe.

anyways, hi!

stop using that hard drive immediately. dont save anything to it, make any more attempts to restore the partition, or anything else that changes what is on the disk.

```
sudo apt-get install testdisk
```

that packages includes two low-level professional grade products from CGSecurity. [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").

to run them, 

```
sudo photorec
sudo testdisk
```

read the documentation at the wiki links above carefully -- 6 years of pictures is vital data! and you will want to recover as much as possible.

using photorec, you will probably not recover the images with filenames intact. "me and becky in 2005.jpg" will become "efja35a.jpg"... things like that.

i suggest trying to recover the vital images with photorec before attempting to recover the partition as a whole... folder names and whatnot is trivial, and the process - if it does not go will - may make things worse. 

once you recover as much of the data as possible and have it backed up somewhere safe, then try to make further changes to the drive that will, hopefully, recover the data en-masse including folder names, partition tables, etc.

---

### Post by cbraxton on 2009-09-25
You might want to try the following:

  [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

If all you've done is format the drive and not actually written any (or much) data to it, photorec may be able to find your pictures for you.

---

### Post by earthpigg on 2009-09-25
> **cbraxton said:**
> You might want to try the following:

  [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

If all you've done is format the drive and not actually written any (or much) data to it, photorec may be able to find your pictures for you.

beat you to it :lolflag:


also, why this works, if you are interested:

by default, most tools dont actually delete any data. they just take down the flags/markers that say "file starts here!" and "file ends here!" while leaving the rest of the ones and zeros on the drive alone. those flags include the file name. if the flags are not there, operating systems see that space as 'available' and will go ahead and save a new file there with new flags - this is why it is essential not to do anything to that drive right now.

photorec looks for patterns in the flag-less data that indicate a document, image file, video, text file, etc.... then copies that potential .jpg, .txt, .avi, etc, file to where you tell it to. (obviously, dont tell it to send the recovered files to the hard drive you are recovering them from immediately.) many of the files it recovers will be false positives or rubbish.

hence, if you ever want to truly wipe a hard drive immediately, you need to use a low-level tool to write zeros to the entire disk.... the FBI and your girlfriend can both use photorec, ya know? :lolflag:

---

### Post by cbraxton on 2009-09-25
> **earthpigg said:**
> beat you to it :lolflag:

Yep, a little slow on the draw on this end! (Also I was not sure if photorec was in Ubuntu repositories or not.)

I've used photorec in the past and have gotten good results with it as long as the desired files have not been overwritten.

---

### Post by Roclemir on 2009-09-27
Thanks guys. Running Photorec now - being 1TB it's estimated time is 20hrs. I'll update tomorrow Afternoon about how it went. Oh, and BTW, i did start to use O&O software, it found the partition fine and everything, but i figured bugger waiting for another trial version of a windows program for another 20hrs for it to tell me to buy it again when there's perfectly good open source items to use, but thanks for the help anyway.

---

