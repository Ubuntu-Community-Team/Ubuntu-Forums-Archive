---
title: "How do I do a full backup/restore?"
date: 2009-11-08
forum: General Help
---

### Post by Lucky75 on 2009-11-08
Hi all,

So I recently upgraded to 9.10, but I was notified that I had many bad sectors on my disks.

I was going to buy a new one.

How do I do a full backup and move all my data to a new disk? Are there utilities, or would I just do a straight copy. I want to move everything and keep it all as it was, just on a new disk. There might be problems if I just do a straight copy due to the bad sectors. Would it be easier to just take an image of it or something?

Thanks!

---

### Post by blueridgedog on 2009-11-08
There are two paths that spring to mind:

1.  Use dd
2.  Use remastersys

Question:  why do you want to do a full backup rather than just your home directory?  If I were facing your issue, I would install the new disk, do a full Ubuntu install, then mount the old disk and copy over any files you wanted.

If you want to use dd, that requires that each disk is installed and working.

Remastersys (available in the repos) will make a bootable DVD that will do a reinstall just like your current system.

---

### Post by slakkie on 2009-11-08
I would use clonezilla for that.

---

### Post by Lucky75 on 2009-11-08
Well, I have a bunch of other services and stuff running that took a while to configure properly. Similarly, I have a website running with a bunch of sql databases that would be painful to fix.

Can you suggest a better way? There were many, many things that I've done to my system (and installed) that I forget about now, but would like to keep. How can I make sure that I keep all of it, unless I copy it all?

---

### Post by blueridgedog on 2009-11-08
I can't think of an auto-magical way to replace a drive with bad sectors, however, the usual suspects are:

dd (a good write up: [http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html](http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html))
systemimager ([http://www.howtoforge.com/howto_linux_systemimager](http://www.howtoforge.com/howto_linux_systemimager))
clonezilla ([http://clonezilla.org/](http://clonezilla.org/))

---

### Post by Lucky75 on 2009-11-08
HMm,thanks for the help guys.

I just did a clean install and then mounted the old disk externally and copied everything over. *almost* have it working again. Copying 1.5 TB of data is a pain in the ***.

---

### Post by blueridgedog on 2009-11-08
Well, don't feel bad.  I did the same.  I was coasting happily on my 8.10 install and took the plunge for 64 bit 9.10.  Now I have 1T worth to get back off of backup drives.

---

### Post by juky on 2010-01-03
[This one](http://ubuntuforums.org/showthread.php?t=35087) is fastest and simplest one. Read it carefully, it is easy.

Cheers,
juky

---

### Post by Manyette on 2010-01-03
I would be hesitant abuot using tar with Karmic.  It has failed to boot for me on a couple of different tries using this guide.

---

