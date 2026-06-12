---
title: "Deleting folders that &quot;don't&quot; exist"
date: 2011-06-26
forum: General Help
---

### Post by vyco10 on 2011-06-26
I alluded to this in another help thread that I had posted, but no one seems to be responding to it there.

My problem is that I have a folder that had been "lost", meaning that it isn't seen by either Windows or Ubuntu. I was able to recover the data from the folder by using a program off the Ultimate Boot CD for Windows called Handy Recovery, but I don't know how to get rid of the folder and files I had backed up. "What's the problem if it's gone?" you might ask? Because the hard drive space is being taken up with the files. I can't access these files, yet they are still there taking up space.

What programs are available on Ubuntu that will get rid of these files (and these files *only*) without wiping out the partition?

---

### Post by noah++ on 2011-06-27
Can I ask how you ascertained that the files are still occupying disk space?

---

### Post by vyco10 on 2011-06-27
> **noah++ said:**
> Can I ask how you ascertained that the files are still occupying disk space?

First, a little background info: [http://ubuntuforums.org/showthread.php?t=1788726](http://ubuntuforums.org/showthread.php?t=1788726)

I had just under 400GB available space on the partition I stored them on. I now have just under 300GB available space on the partition and those files were the last thing that I put on that partition before I began this ordeal. And how I know they're still there is because I, as I said in the first post in this thread, recovered them. I just can't see *or* delete them when logged in to either Windows or Ubuntu.

---

### Post by varunendra on 2011-06-27
While that drive is mounted, try disk usage analyzer in super-user mode to determine which files have occupied the space:
```
gksu baobab
```

---

### Post by vyco10 on 2011-06-27
> **varunendra said:**
> While that drive is mounted, try disk usage analyzer in super-user mode to determine which files have occupied the space:
```
gksu baobab
```

The result of that query, as in *what* was taking up *how much* space, was the same as what is listed on the File System properties page of the drive's partition, 424.1GB out of 813.3GB:

[IMG]http://i247.photobucket.com/albums/gg122/vyco10/SystemSpaceScreenshot.png[/IMG]

The curious thing here is that it lists 41,047 items totaling 424.1GB, yet it says that 530.4GB are used with **284.0**GB of free space. I don't know about your calculator but mine here says that 814.3 minus 424.1GB equals 390.2, not 284.0. But when I subtract 530.4 from 814.3 I get **283.9**.

Not only do I have this math here to indicate to me that the files are still there but I have an external drive full of the files I recovered from that lost folder via the program I mentioned called "Handy Recovery". 

The files are there, but something had to have happened to the record pointing to the files when Windows MBR got fubar'd. Neither operating system (Windows or Ubuntu) will display the folder or the files. They're there, as the math and my lack of hard drive space shows, but they aren't accessible by any typical means.

What I want to know is if there is a way to delete these files from the hard drive without reformatting the drives.

---

### Post by Jouke74 on 2011-06-27
I assume that the file system is NTFS? 
Please remind yourself that there is a part of the disk used by the file system itself. 

If Windows is also using this disk then you will have hidden recovery data, swapfile for windows etc. You won't see those in Windows, but they should be seen by Ubuntu .. hmm.

Also a lot of small files will add to the size difference. 
E.g. on disk a cluster of 4096 bytes will be used for any files between 0 and 4096 bytes.

I would first run a chkdsk in Windows to fix the NTFS partition.

To get rid of it the easiest way is to copy all data to an external drive and unfortunately reformat it.

---

### Post by vyco10 on 2011-06-27
> **Jouke74 said:**
> I assume that the file system is NTFS?

Yes, it's NTFS.
 
> **Jouke74 said:**
> Please remind yourself that there is a part of the disk used by the file system itself.

If Windows is also using this disk then you will have hidden recovery data, swapfile for windows etc. You won't see those in Windows, but they should be seen by Ubuntu .. hmm.

Also a lot of small files will add to the size difference. 
E.g. on disk a cluster of 4096 bytes will be used for any files between 0 and 4096 bytes.

Yes, I'm aware of this. I know how my system is set up, how much the swap file is (*and where it's located*), etc. None of that should equal *100GB* of hard drive space. 

Again, I know what's taking up the space, or at least that the space is being counted as taken. I just need to find a way to free up the space without reformatting.

> **Jouke74 said:**
> 
I would first run a chkdsk in Windows to fix the NTFS partition.

I'll try that and post whether or not it has any effect.

> **Jouke74 said:**
> 
To get rid of it the easiest way is to copy all data to an external drive and unfortunately reformat it.

It's not easy if you don't have another hard drive available with enough free space to accommodate all of your data, which I don't. That's why I posted this thread. If I had another drive I would've just reformatted and bypassed the headache of coming to a help forum. ;)

---

### Post by varunendra on 2011-06-27
Fair enough. But I referred to disk usage analyzer (in super-user mode, as it is important!) just because when it shows how much space is occupied, it also shows the names (in a typical hierarchical tree) of the files that occupy that space.

For that detail, you have to click the "Scan Folder" icon, then browse to the folder/drive you want to scan. It'll then take its time to scan then come up with the tree telling you name of every individual file that adds up to occupy that space. Guessing from your posts I assume that you already are familiar with 'hidden' files/folders and how to show them in ubuntu. Once you get the list, you can confirm whether or not they are the same files as you recovered.

I also assume that it is an ntfs partition. Have you tried **chkdsk /x /f** in windows to correct possible errors on it?

As for the mathematics involved in the file size and occupied size, this 'can be' explainable. One possible explanation is the 'bolck size' alotted to each file. It is the minimum space that has to be alotted to a file. No two files can share one block. For example if a file is 2KB in size, but the block size for that partition is of 4KB size, then the combined file size of four such files would be:[INDENT]4 x 2KB = 8KB
but the space occupied on disk :
4 x 4KB = 16KB
[/INDENT]There may be other reasons, that's just one of the possibilities. :)



**EDIT:**
Oops! Looks like I must increase my typing speed :lolflag:

---

### Post by varunendra on 2011-06-27
> **vyco10 said:**
> It's not easy if you don't have another hard drive available with enough free space to accommodate all of your data, which I don't.
If you have some really important data on that drive, try compression tools like 7zip to reduce their size and/or make room on your external drive. Because you don't know what chkdsk will do to your files if it tries to repair the partition table/possible bad sectors.

---

### Post by vyco10 on 2011-06-27
> **varunendra said:**
> If you have some really important data on that drive, try compression tools like 7zip to reduce their size and/or make room on your external drive. Because you don't know what chkdsk will do to your files if it tries to repair the partition table/possible bad sectors.

So what I need to do is basically highlight all the folders that exist on that partition (*non-system partition, obviously*) and... add to archive?

Btw... the external drive is only 80GB. I was just using it to ferry the recovered files from the lost folder to Ubuntu.

---

### Post by varunendra on 2011-06-27
> **vyco10 said:**
> So what I need to do is basically highlight all the folders that exist on that partition (*non-system partition, obviously*) and... add to archive?

Btw... the external drive is only 80GB. I was just using it to ferry the recovered files from the lost folder to Ubuntu.

Umm.... kinda 'yes'..
Instead of typing a long story, I think this example may help you find your way around it: [http://ubuntuforums.org/showpost.php?p=9483380&postcount=29](http://ubuntuforums.org/showpost.php?p=9483380&postcount=29)
[note: skip unnecessary steps that don't match your case]

---

### Post by psusi on 2011-06-27
Run chkdsk from windows and if that doesn't fix it, the files must be there somewhere; you just have to find them.

---

### Post by vyco10 on 2011-07-14
Just to follow up with this, instead of risking losing data by running chkdsk... I just junked the Windows installation on my laptop and used the hard drive from it (300GB) along with the 160GB hard drive in my desktop and a couple of 40GB 2.5 hard drives that are in portable encasings and just did the backup/reformat thing.

So, I don't know whether or not this should be tagged as "solved" or not.

---

