---
title: "CRAP!  Partition seems gone with Ubuntu/XP Dual-Boot :("
date: 2011-01-30
forum: General Help
---

### Post by malenkylizards on 2011-01-30
Hello all,

I have two 1TB drives in my system.  One is divided into two 500GB partitions, one of which holds my Ubuntu system, the other of which holds my XP system.  The other drive is also divided into two 500GB partitions, one of which is for Ubuntu data, the other of which will be for XP data, but is now empty.  This is a system I'm in the process of setting up now.

What is currently the system drive previously held my data, which I copied onto the Ubuntu data partition.  After I copied the data over, I formatted the system disk, installed XP and then Ubuntu.  With both operating systems installed, I went into Ubuntu to start setting things up...But the Ubuntu partition seems to be gone!  The drive now has a 500 GB NTFS partition, and 500 GB of free space.

I don't know where the NTFS partition came from, but it has nothing but what I assume are Windows system files in it:
- System Volume Information folder
AUTOEXEC.BAT
boot.ini
CONFIG.SYS
IO.SYS
MSDOS.SYS
NTDETECT.COM
ntldr

My fear is that Windows decided to make that partition its own.  Greater than that fear is the one that I accidentally told it to do so.  :(

Are there any recovery options at this point?

---

### Post by [Snc] on 2011-01-30
> **malenkylizards said:**
> Hello all,

I have two 1TB drives in my system.  One is divided into two 500GB partitions, one of which holds my Ubuntu system, the other of which holds my XP system.  The other drive is also divided into two 500GB partitions, one of which is for Ubuntu data, the other of which will be for XP data, but is now empty.  This is a system I'm in the process of setting up now.

What is currently the system drive previously held my data, which I copied onto the Ubuntu data partition.  After I copied the data over, I formatted the system disk, installed XP and then Ubuntu.  With both operating systems installed, I went into Ubuntu to start setting things up...But the Ubuntu partition seems to be gone!  The drive now has a 500 GB NTFS partition, and 500 GB of free space.

I don't know where the NTFS partition came from, but it has nothing but what I assume are Windows system files in it:
- System Volume Information folder
AUTOEXEC.BAT
boot.ini
CONFIG.SYS
IO.SYS
MSDOS.SYS
NTDETECT.COM
ntldr

My fear is that Windows decided to make that partition its own.  Greater than that fear is the one that I accidentally told it to do so.  :(

Are there any recovery options at this point?

Windows says EXT is available "free" space (or not formatted ... you choose)

Is there any way, you could boot a live CD or live USB?

That way, you could get a look at the real image and not just what windows wants to tell you ...

Post back the results...

---

### Post by malenkylizards on 2011-01-30
I do have the Live CD, so I could boot into it, but I might not have made myself clear.  Ubuntu is installed, I'm doing all this in Ubuntu, and it only sees three partitions:

system disk:
/dev/sdb1: 476 GB NTFS (On which XP is installed)
/dev/sdb2: 524 GB ext4 (On which Ubuntu is installed)
data disk:
/dev/sda1: 500 GB NTFS (This is where I expect my data was/is)
*Free, 500 GB* (This is because I hadn't created the fourth partition yet)

Now, the Disk Utility has a couple of things to say about sda1, which confuse me: The partition type is listed as W95 FAT32 (LBA) (0x0c), but the type is listed as NTFS.

I DID initially format the data partition as FAT, thinking it would let me access the data on that drive from both operating systems, which certainly suggests that it's where I put all my stuff.  I just can't seem to access any of that, and all that shows up in the drive are the 8 windows items I listed previously.  So, is there anything that Ubuntu would be hiding at this point?

---

### Post by [Snc] on 2011-01-30
> **malenkylizards said:**
> So, is there anything that Ubuntu would be hiding at this point?

I doubt, that Ubuntu would hide anything, have you tried listing all files?
```
ls -a
```
maybe some are hidden.

---

### Post by malenkylizards on 2011-01-30
No new result with "ls -a".  That's not quite what I meant.  I thought that whatever happened, it might've been lazily deleted; that is, the missing stuff is in a place that has been marked as available for overwriting, but hadn't actually been overwritten.

---

### Post by malenkylizards on 2011-01-31
Bump.

I am assuming that this partition is a goner, and will wait 24 more hours before marking this thread as solved.

---

### Post by ubername on 2011-01-31
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

Might be worth a try

---

