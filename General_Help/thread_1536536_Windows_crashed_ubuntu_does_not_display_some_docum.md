---
title: "Windows crashed: ubuntu does not display some documents"
date: 2010-07-22
forum: General Help
---

### Post by nohxpolitan on 2010-07-22
Hello!

So the other day my Dell laptop completely crashed, rebooted, got a DST error, tried to run a dskchk off the Windows Boot CD, failed due to "unrecoverable files".  Then booted off Ubuntu to salvage my stuff, which seems to work fine, and I can even see my HD - "120 Gb Drive" or whatever it says.  When I open it, I see 2 folders: windows, Epson, and 2 random files.


Here's the thing.  It says 108/120 gigs are taken, which is just how I left my HD with all my stuff on it that I am trying to recover.  Yet my personal and important documents (pictures, videos, documents and even music) are NOWHERE to be found and searches bring up nothing.  yet it says the disk space is taken...I am at a total loss.

Has anyone encountered this or perhaps have any solutions? I have some extremely important documents that I will never not backup again in the future...

thanks for your time!

---

### Post by quixote on 2010-07-24
> important documents that I will never not backup again in the future.Yup.  I know how that feels! :shock:

The fact that it's showing the space as occupied means that all your files are very likely there and intact.  There are ways to recover files even if the partition table is gone (the disk's own data about where everything is). There's a very good run-down here: [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

If you boot from a liveCD, open a terminal, and type ```
sudo fdisk -l        *[that's "l" as in "list"]*
```what does it say about your main 120GB drive?  Does it even see it?  

Also, how did you have your files arranged?  Windows, data, and Ubuntu on separate partitions (or "drives")?  Just Windows, and you're using Ubuntu only from a liveCD?  Or some other arrangement?

---

### Post by Mark Phelps on 2010-07-24
They're your documents; it's your choice how to recover them.

But, in doing such stuff for years, I've learned an interesting lesson: MS Windows utilities are better at recovering files from NTFS partitions, Linux utilities are better at recovering files from Linux partitions.

You can mess around for several days trying to use testdisk and photorec -- and in the process, render your drive completely unrecoverable.

OR, you can do the following:
1) Remove your drive from your machine, NOW.  The more you use it, the more chance you'll ruin an chance of data recovery
2) Download GetDataBack from Runtime Software (a free download) and install in on another MS Windows box
3) Connect your drive to the other MS Windows box
4) Run the GetDataBack app and see what it is able to find.  Be patient!! With 108GB to search, it is likely to take ALL NIGHT to scan the entire drive.
5) IF it finds all your important files, then you are lucky.  

NOW, you have to decide if your "personal and important" data is worth $80 to get it all back -- because that is what the commercial version of GetDataBack costs.

I've used their product several times, and every time, it was able to recover ALL the files from the corrupted drive.

It's your money; it's your choice.

---

### Post by Goolie on 2010-07-24
If you have any means, i.e. friends or other methods of acquiring Norton Ghost, I found that to work for Windows partitions and recovers files remarkably well.

---

