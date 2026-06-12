---
title: "Rebuilding Partitions and Grub"
date: 2009-07-19
forum: General Help
---

### Post by Kaneda on 2009-07-19
I am dual-booting Vista and Ubuntu 8.04 using GRUB

I was messing around with some programs while logged into Vista, trying to make a bootable USB drive to work with my new Eee PC.  I was doing all of this on my main computer, and everything seemed to be working fine.  Then last night when I was done with everything, I shut down as I normally do.

This morning when I turned my computer on, my computer didn't go into grub and gave me an error saying that it couldn't boot up because there was no valid operating system on the hard drive.

The first thing I did was go into BIOS and run a hard disk diagnostic.  It passed.

So, I popped in a Knoppix CD to see if I could get in and fix things.  When I typed ```
sudo fdisk -l
``` it gave me no output whatsoever.  I tried mounting my ntfs and ext3 partitions, but nothing worked.

Then I came across [this]("http://ubuntuforums.org/archive/index.php/t-24113.html") post.  I popped in my Ubuntu CD and went through to the partition drives section.  It was displaying that I only had one partition and it was telling me that it was empty.  There was no way to mount my partitions from there.

Then I tried the second option listed in that post, and I went into the live CD, opened up the command prompt, and typed:
```
grub
root (hd0,0)
```
It said that drive didn't exist, so I also tried (hd0,1) through (hd0,6)... nothing.

Anyway, considering everything was working normally until I shut down my computer and rebooted, I get the feeling that all of my data is still there somewhere, but the computer seems to think that my HDD was wiped clean.

Does anyone know how I can restore this?  I'd rather not format my hard drive and reinstall everything if I don't have to.  (at least I have backups for my important stuff)

Any help would be GREATLY appreciated!  Thanks.

---

### Post by merlinus on 2009-07-19
You might try testdisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by emeraldgirl08 on 2009-07-19
Have you tried using [SuperGrubdisk???](http://www.supergrubdisk.org/index.php?pid=5)

Not sure if that would work but I'm sure if the partitions still do exist this would find them.

---

### Post by Kaneda on 2009-08-02
Well, I used testdisk, and I was able to get in and backup all my stuff, but I was getting frustrated at trying to get things back to the way they were (spent all day) so I just formatted my HDD and re-installed everything, putting my backed up files in later.

Thanks for your help guys!

---

### Post by merlinus on 2009-08-02
Glad to hear that at least you were able to rescue your data.  It reminds me to do regular backups, and not be lazy.

Have fun, and post back if you run into other difficulties.

---

