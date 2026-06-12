---
title: "Disk Defragment"
date: 2009-09-25
forum: General Help
---

### Post by arnab_das on 2009-09-25
Is Disk Defragment option available in Ubuntu? Or maybe something like Scandisk.

btw i find that sometimes Ubuntu starts scanning my disk automatically during booting (it says its scanning the hard disk after some 33 times). Is this normal?

---

### Post by mikewhatever on 2009-09-25
There is no defragmentation tool in Ubuntu, and Linux in general. You can read more on that here [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Periodical disc scans are normal. It just checks the file system for errors and fixes whatever it finds.

---

### Post by drs305 on 2009-09-25
Routine scanning is normal. It's done by "fsck" and by default runs every 30 mounts or so. You can control how often it is checked by setting the parameters with an app called tune2fs. You can set it by number of mounts, days, weeks, etc. Read about it in the man pages - "man tune2fs". Whether or not a system is checked or not is set in fstab - the second to last numeric entry (usually 0, 1, or 2). 0 means never check and 2 means to check it with a lower priority than 1.

Defragmenting isn't really necessary in linux - the file system doesn't fragment the way others do.

---

### Post by Zimmer on 2009-09-25
as the Linux System Administrator Guide states, "Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system...

The check made at boot time can be varied somewhere in the configs, but generally the default setting checks a disk when it has been mounted @30 times.

So, although if you install on a system with more than one disk/partition they seem to run in synch for checks, eventually, when you have played about mounting and umounting disks for various reasons, they will NOT all be checked at the same boot (because they may or may not exceed the 30 mounts before checking at the same time)...

---

### Post by cgroza on 2009-09-25
There are programs to defragment in linux but if you use ext3 on your partitions not Fat,NTFS you dont need it...

---

### Post by scouser73 on 2009-09-25
Do Ubuntu user really need to defrag their hard disk like Windows users do?

Answer: No. Linux filesystems like Ext3 have their own unique ways to keep fragmentation level at minimum. Hence, hard disk is not a major factor contributing to the decrease of performance in a Linux system like Ubuntu. This is also a reason why you will see it’s rare for a defragging software to come up with a Linux distribution.

That snippet came from [[COLOR="Red"]**Ubuntu Hard Disk Optimiser**[/COLOR]]("http://www.bloganything.net/982/ubuntu-hard-disk-optimizer-defragmenter")

---

### Post by jerome1232 on 2009-09-25
Does ext3 fragment, yes, just not very much under normal conditions.

Let the drive fill up and you will get heavy fragmentation. Download large torrents that don't preallocate space and you will get fragmentation. Record lots of streaming data and I bet you will get fragmentation.

Ext3 has no defrag tool, ext4 has one in the works, xfs I believe has an online defrag tool. I think jfs has one, but it's not ported to linux yet or something. Anyways if you look into all the filesystems for linux you can find more about their strengths and weaknesses.

---

### Post by pcjunkie on 2009-09-25
If it feels clunky and the disk reads far more than it should make a backup, run the live cd and format the dive then copy them back. 

You will need to chown user:user ~/home/user/

once you are done. 
Try to keep your home folder big if you can and use a separate partition for /tmp.

---

### Post by TrakerJon on 2009-09-25
> **arnab_das said:**
> Is Disk Defragment option available in Ubuntu? Or maybe something like Scandisk.

btw i find that sometimes Ubuntu starts scanning my disk automatically during booting (it says its scanning the hard disk after some 33 times). Is this normal?


Yes, actually there is a good one...

Defrag (or fidefrag I should say)

**sudo apt-get install bzr python-psyco**
**bzr branch lp:fidefrag**
cd fidefrag/src
sudo python fidefrag.py -d /<directory name>

Note: It's not a good idea to defrag your whole system, some directories won't react very well. I typically defrag /usr (this one takes a long time), /var, /lib, /home, /etc, /bin and /sbin

---

### Post by jerome1232 on 2009-09-25
@TrakerJon, love the sig

---

