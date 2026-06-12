---
title: "Recovering a HDD, may have screwed things up, please help!"
date: 2009-08-04
forum: General Help
---

### Post by Megrimn on 2009-08-04
OK... I have been working at recovering some documents from my aunt's hard drive.  For a time, I was able to access the drive and view the files.  Idiot that I was, I tried removing the 6 or 7 TROJANS from the thing, plus some other viruses, before backing up any files.  After that, I cannot access *any* files on it, let alone run 'chkdsk -f' or any thing else (Windows XP is on the disk).  I am assuming that removing the viruses somehow damaged the part of the hard drive that keeps track of the partitions.  I have also tried running 'testdisk' on it, but only an 8G part of it shows up, where the actual hard drive size is about 40G and I know the OS partition is 20G.  

I know now that I should have backed up the files when i had the chance, but I don't have a time machine to go back and change that.  I'm toying with giving up, unless someone here has a solution I haven't tried or a time machine :).  

Thanks in advance, I really appreciate it.

---

### Post by alan34 on 2009-08-05
I had to do similar to a XP machine that had some system files deleted and would not boot. I used a Puppy Linux disc but you could use your Ubuntu live CD, mount the hard drive and transfer the files you want to a usb stick.

Good luck

---

### Post by Megrimn on 2009-08-05
> **Megrimn said:**
> **_*For a time, I was able to access the drive and view the files.*  Idiot that I was, I tried removing the 6 or 7 TROJANS from the thing, plus some other viruses, before backing up any files.  After that, I cannot access *any* files on it._**

...

---

### Post by Megrimn on 2009-08-08
bump

---

### Post by GreenBowlPacker_3 on 2009-08-08
I had a similar problem before and this is the only way I could fix it.  This may not be the route you want to go, but it works. If you have access to windows run "diskmgmt".  Here you can check the allocations of the drive.  I had to reallocate all of my partitions then allocate them back to one drive and format it.  After that you can use the program "Recover My Files" to recover what was on it before the format.  I got back about 90% of my files that way.  You can get a free version on the program online.  I know it isn't exactly legal, but I found a key code that allowed me to get the full program in order to save the files.  This was a last resort for me, I really needed the files for work.  Hope it helps you.

---

### Post by Megrimn on 2009-08-10
> **GreenBowlPacker_3 said:**
> I had a similar problem before and this is the only way I could fix it.  This may not be the route you want to go, but it works. If you have access to windows run "diskmgmt".  Here you can check the allocations of the drive.  I had to reallocate all of my partitions then allocate them back to one drive and format it.  After that you can use the program "Recover My Files" to recover what was on it before the format.  I got back about 90% of my files that way.  You can get a free version on the program online.  I know it isn't exactly legal, but I found a key code that allowed me to get the full program in order to save the files.  This was a last resort for me, I really needed the files for work.  Hope it helps you.

Thanks, I may try that, but will look for similar free software if possible.

[edit] I found this page, I am trying the apps mentioned here: [http://lifehacker.com/393084/how-to-recover-deleted-files-with-free-software](http://lifehacker.com/393084/how-to-recover-deleted-files-with-free-software)

---

