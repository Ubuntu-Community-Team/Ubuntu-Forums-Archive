---
title: "Pointers for adding second SATA Drive?"
date: 2009-08-15
forum: General Help
---

### Post by longtex on 2009-08-15
I just stuck a 1.5TB SATA drive in this Ubu 8.10 box (no, THIS one, right here, the one I'm typing on), and so far, so good. It shows up in gparted as a 1.36 TB drive, /dev/sda (my boot drive which is a 250GB SATA shows as /dev/sdb).

Now, before I partition it and proceed, I'd like to ask the community for any ideas you might have, on things I should be careful to add... or avoid.

My intention with this drive is to use it to contain media for my home network, comprising four Linux boxes (including this one) and three fulltime Win XP boxes (his, hers, and "plug your i[hone into this one - it's sacrificial") plus occasional wireless visitors, mostly Win XP/Vista or Mac laptops.

Should I split the drive in two or more partitions, or keep it all one? Pros, cons each way?

I'm assuming the thing to do here is to use Samba to share the files with the Wins (one of whose jobs is to broadcast audio media on a little stereo FM xmtr). Is there any good reason to have multiple shares versus one with rationally laid out directory structure? What about counts of files per directory/subdirectory - any serious issues there? 

Any other considerations?

THanks - Tex

---

### Post by Bradj47 on 2009-08-15
The only reason I always keep my drives one partition is because I know nothing about GRUB and I don't want to mess with it. When I first tried to partition my SATA drive I tried to figure out how to get GRUB to display an option of operating systems to boot up but I failed miserably. I currently have 2 hard drives on this box (this one, the one I'm typing on right here ;) ) ; a SATA and an IDE, the SATA has Ubuntu, the IDE has Solaris. I just change the boot priority in the BIOS depending on what I want to boot. So if you know how to handle GRUB and all that without messing anything up, I say go for it. Plus its a TB hard drive so if it were me (and I knew GRUB better) I'd put a ton of operating systems on there to mess around with just to get to know how they all work.

---

### Post by capscrew on 2009-08-15
> **longtex said:**
> ...
Now, before I partition it and proceed, I'd like to ask the community for any ideas you might have, on things I should be careful to add... or avoid.
...
Any other considerations?


Take a look at the documentation for adding a new drive [_[COLOR="DarkSlateGray"]here[/COLOR]_]("https://help.ubuntu.com/community/InstallingANewHardDrive").  

I would eliminate the 5% root reserved space.  There is no need for root reserved space on a data partition.  I format my drives at the CLI with the mkfs command.  I 'm just guessing, but I bet you can remove the reserved space using gparted too.

How many partitions you have is really up to your needs. Partitions are more for administrative convenience.

EDIT: RE: Bradj47 -- No need to worry about GRUB if the drive (and whatever partitions you have on it) is for data only.  GRUB is only needed when booting an OS.  You will have to mount the partitions to the booted OS's filesystem.

EDIT2: Opps missed this point > Is there any good reason to have multiple shares versus one with rationally laid out directory structure? What about counts of files per directory/subdirectory - any serious issues there? 
 The Samba "share" becomes the root point for the user.  The Linux OS filesystem is important but not the primary concern.

I have all of my samba shares on a separate partition (on an external drive) that is mounted at /smb.

---

