---
title: "GUI backup solution?"
date: 2009-07-29
forum: General Help
---

### Post by Ck.asdf on 2009-07-29
Hello.  While I am getting better with BASH, I still don't know nearly as much as I'd like to.  Therefore, I'd like to ask you all for GUI backup solutions.

I've reviewed a few, such as FlyBack, Backula, rsnapshot, and TimeVault.  From what I've read, Backula is for extremely advanced system admins, and TimeVault may not work as well for laptops needing to back up to external (USB, network, etc) storage.


Anyway, my partitions on both my desktop & laptop are as follows:

> Windows
Ubuntu
Storage (docs, music, vids, etc)

Desktop = Ubuntu 9.04
Laptop = Ubuntu Studio 8.10

I would like to run backups from my laptop to my desktop, as I think I may remove Windows from the desktop & use it as an all-purpose server.
I would like to have different schedules for different folders, such as:

/media/Storage/documents     #every night
/media/Storage/projectFiles  #once a week
/media/Storage/audio         #once a month
/media/Storage/video         #once a month

Also, I'd like the possibility of doing this over Ethernet or wireless, and to check the files for integrity/validity/whatev.  Basically, see if their MD5 sums equal that of the original source data.  I've done a few drag & drop copies in the past when I didn't know about corrupted copies, and I've ended up with a few music albums that read 0 bytes, as well as a few other items, and I'd like to make sure it doesn't happen again.


I'd also like another schedule that takes those daily documents and stores them in folders that either are numbered 0-6/1-7 or labeled "Sunday - Saturday" so I have a different backup each day.  Finally, every week the documents folder with daily sub-folders would get renamed to "last" week, so I'd have one week of backups at the least, two weeks at the most, depending on when it is during the week.
Which actually that, I might be able to write a script for as I did the same thing for a Windows backup at the location I used to work.


Oh, and one more thing: I've seen some of these backup solutions that compress the files or otherwise make them unusable.
I'm thinking maybe in addition to being a backup from my laptop, I could use my desktop as a media streaming computer so that my xbox, others' laptops, etc can browse the media, so I want to be able to make this an uncompressed regularly readable format.


Suggestions? Sorry for the immense amount of text!  Thanks for any help. :)

---

