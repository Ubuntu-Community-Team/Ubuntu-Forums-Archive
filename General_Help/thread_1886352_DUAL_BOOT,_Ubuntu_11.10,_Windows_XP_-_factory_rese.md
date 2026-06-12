---
title: "DUAL BOOT, Ubuntu 11.10, Windows XP - factory reset not working"
date: 2011-11-24
forum: General Help
---

### Post by LadySapphira on 2011-11-24
Hi everyone.  Was wondering if anyone else has run across something like this dual booting or has advice.



I dual boot Ubuntu 11.10, and Windows XP.  It worked GREAT, I can read-write to windows.  but Windows got a horrible trojan I can't fix (I was dumb and didn't update java - learned my lesson the hard way).


I went to factory reset, like normal.  I went to the partition it's on but it can't "find" the file required.  So I can't factory reset Windows.  I can't get into windows without it crashing within one minute, if I can get it up at all (even safe mode).  So I really want to factory reset.  I can access all files from Ubuntu so I'm ok in that sense but... I want my computer working fully again.



Any advice or previous experiences like this? What might be causing this?

---

### Post by Metamence on 2011-11-24
[http://www.howtogeek.com/howto/31804/the-10-cleverest-ways-to-use-linux-to-fix-your-windows-pc/](http://www.howtogeek.com/howto/31804/the-10-cleverest-ways-to-use-linux-to-fix-your-windows-pc/)

Maybe that link would be of some help?

---

### Post by sammiev on 2011-11-24
You can use install Bitdefender or Avast into Ubuntu 11.10 and scan the full hard drive. :)

---

### Post by Mark Phelps on 2011-11-24
Both Avira and Kasperky provide free ISO images you can download and burn to CD to then boot and run antivirus scans.  You should check them out.

As to factory reset, either you have a set of CDs to do that, or your PC came with a Recovery partition containing a compressed Windows image.

Seeing as how it's XP, it's more likely to be the former -- but you will need to check the documentation on your PC to see what you need to do for a factory reset.

Also, if you have a Windows install CD, then you might be able to do a Repair Install -- which will reinstall XP but leave your apps, data, and settings intact.

---

### Post by LadySapphira on 2011-11-25
It's windows XP pro edition, it has a recovery partition.  The partition, when opened either through windows or through grub can not find a file it needs in order to work :confused:  (I've done this many times before).


I don't care about programs etc - I kind of want a full clean install, especially after running multiple antivirus including root kits, finding stuff in the root, getting rid of them and they pop back up again.


Should have made this clear, but I've already backed up both my windows partition and ubuntu documents.  I can access and write to all files in windows but the system itself won't work (<3 ubuntu for letting me get all my files)

Thanks for the links - will check out avast.




but a thought... I don't understand why windows recovery partition won't work.  That's really all I want so if anyone can think of a reason/ fix that would be great

---

### Post by sammiev on 2011-11-25
For Avast you can check out [this]("http://ubuntuforums.org/showthread.php?t=1870666&highlight=avast") post. Read post #6 if you have any problems. :)

[Bitdefender]("http://download.bitdefender.com/repos/#") if needed. :)

---

### Post by Mark Phelps on 2011-11-26
> **LadySapphira said:**
> but a thought... I don't understand why windows recovery partition won't work.  That's really all I want so if anyone can think of a reason/ fix that would be great
IF you repartition your drive, that often will cause the older Restore utilities to fail -- because they can't make sense of the Linux partitions and need to repartition that space in order to do the restore.

If you boot with an Ubuntu desktop CD, choose the Try Ubuntu option, and then use the Disk Utility to remove all the Linux partitions, it is likely that Restore will work again.

---

### Post by LadySapphira on 2011-12-04
> **Mark Phelps said:**
> IF you repartition your drive, that often will cause the older Restore utilities to fail -- because they can't make sense of the Linux partitions and need to repartition that space in order to do the restore.

If you boot with an Ubuntu desktop CD, choose the Try Ubuntu option, and then use the Disk Utility to remove all the Linux partitions, it is likely that Restore will work again.

Thank you.  That seems a good option.

---

