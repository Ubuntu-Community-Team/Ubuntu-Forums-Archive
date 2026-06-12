---
title: "read-only root and can't edit fstab"
date: 2010-04-19
forum: General Help
---

### Post by doodude on 2010-04-19
I don't know how it happened, but I was unable to boot into Ubuntu 9.1 today because the file system is now read only.  When I check fstab, it shows "ro" but I can't change it because it's on a read only file system.  I tried umounting the root then remounting with read/write access, but I was unable to umount the root.  I also tried booting with a live CD, but all I can find is the root.disk file, I can't see any of the file structure.  That's probably just how it is supposed to be, but I'm new to Linux so I found it strange.  

Can anyone suggest another method to either change the disk to read/write besides this?
[INDENT]sudo umount /
mount -o remount,rw /
[/INDENT]

The other option would be to somehow mount the disk image while using a live CD so that I can get to the fstab file and (hopefully) edit it.

Thanks for any suggestions.

---

### Post by darolu on 2010-04-19
You won't be able to unmount "/" when you are using it to boot; you will have to make your changes using a LiveCD/bootable pendrive. The default options for "/" (fstab file) are "errors=remount-ro", so it only mounts read-only when erros are present, try running a file system check (booting from LiveCD, without mounting it) with e2fsck (change your device accordingly):
```
$ e2fsck /dev/sda1
```

---

### Post by doodude on 2010-04-19
Thanks for the suggestion.  When I run a live CD and use the command you suggested, I get:
"Superblock invalid, tring backup blocks...
Bad magic number in super block while trying to open /dev/sda1
The superblock could not be read or does not describe a correct ext2 file system..."

When I look at GParted, the two file systems are both NTFS.  I have a root.disk image file under /ubuntu/disks that is the size of the file system created when I originally installed ubuntu.

The disk has been failing (bad sectors) for months, so that maybe that's related to this problem, but I think it's probably something I changed without knowing when I was looking at the partitions before the problem started.

Is there a way I could mount that image file to get to the files while using the live CD?  I really don't understand how ubuntu is residing on an NTFS partition... but again, I am a linux newbie.

Thanks

---

### Post by klemes on 2010-04-19
You don't describe your exact situation well enough for someone to be able to help you.
Did you install Ubuntu with Wubi or is it a native install?
What type of filesystem did you originally specify when you first installed Ubuntu?
What exactly is this image file you want to mount?Is it a backup?If yes how you acquired it(what tools did you use?)
Anyway a good place to start would be to start from Live CD as you did and type :

```
sudo fdisk -l
```

to see all available partitions in your hard drive.
and then run a sudo fsck /dev/sdxx according to what partition the previous command will point out as being your root partition.
Also if you are able to mount eventually your / partition it would be nice to show us the /etc/fstab file and the output of the blkid command though I doubt it it's a fstab problem rather being a hard disk failure as you also suspect...

---

### Post by doodude on 2010-04-19
I apologize for my ignorance here.  I'll try to give some background:

I tried sudo fdisk -l and get the following results:

[INDENT]Device Boot    Start    End    Blocks        Id   System
/dev/sda1  *    1      18650    149806093+   7    HPFS/NTFS
/dev/sda2       18651  19457    648227+      7    HPFS/NTFS[/INDENT]

I installed from a live CD and I honestly don't recall what file system I setup at the time.  Since neither of these partitions are ext3, maybe that means I used Wubi (though I never remembered seeing that term until you posted it).

As for the image file, I guess I'm trying to understand what's going on when I boot into Ubuntu and where that directory structure resides.  When I attempt to boot normally and end up at a terminal after the GUI load fails and has several error messages about a read only file system.  

The fstab file says this :
[INDENT]UUID=19E45XXXXXXXXXXXX /host ntfs-3g defaults 0 0
UUID=2CXXXXXXXXXXXXXXX / ntfs-3g users,ro 0 0[/INDENT]

Thanks
(not actually X's, but I'm assuming that isn't important)

I've copied all the files I care about to a backup drive, so I might just do a new installation, but now I'm not sure how to even do that as the live CD didn't give me the option of installing without formatting the drive.

---

### Post by louieb on 2010-04-19
You have a WUBI (inside windows) install. Sorry - have not used it - it been said - easiest way to install Linux and the hardest to fix when things go wrong.

Perhaps this will help [WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

think this might be the section you want
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

---

### Post by doodude on 2010-04-20
Thanks,  I'll check out the wubiguide tonight.  At least that explains why I haven't been able to make sense of the lack of ext3 partition...

The other option (now that I have the files I care about) is that I delete that root image and do a fresh install on a new partition.  Is there a convenient way to resize then add a partition in Ubuntu?  I currently have 2 NTFS partitions (one big, one small).  There's plenty of space on the big one so I could resize it and move the partitions over to make room for a new one on which I can install Ubuntu.  I know I used to be able to do operations like this with partition magic.  Is there a ubuntu equivalent (or command line method)?

Thanks again for everyone's help!

---

### Post by louieb on 2010-04-20
The guide refers to a program called LVPM that can convert a wubi install to a normal one. If it were mine I'd probably do a fresh install. 

Gparted is my open source partition editor of choice. Its on the Ubuntu live CD. It has a pretty easy to understand graphical interface. You will need to know the difference between logical, extended, and primary partitions - but thats easy to learn - [Partitions 101]("http://louboldt.com/ilinuxpart.htm")   

Although the Ubuntu live CD has it - I usually use a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") or [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  - they will usually have the newest version of Gparted.  

Which flavor of windows are you running? When you shrink the NTFS partition - there is a flag - align to cylinder boundary - leave it checked for XP - uncheck it for Vista and Win7.

---

### Post by 3rdalbum on 2010-04-20
The Ubuntu installer (when running Ubuntu from the disc) has a partitioner inside it, that can resize partitions.

Your problem sounds like there's some filesystem damage to the Ubuntu installation (which is inside that root.disk file). It's probably possible to use the live CD and then run fsck  on the root.disk file. First, boot up the live CD and navigate your file browser to where the root.disk file is. Then open a terminal and do the following:

```
sudo fsck <drag the root.disk file into the terminal and hit Enter>
```

I'm not sure if this will work, but you can give it a go.

---

### Post by doodude on 2010-04-21
Wahoo!  I found a default wubi fstab file and tried it and viola, everything is back to normal.  Girlfriend is happy to have her PC back, so I'm happy.

Thanks for everyone's help.  I really like Ubuntu, but there is a learning curve to overcome... So far, I'd say it's been worth it despite the time I've spent on this.

---

### Post by john_3000 on 2010-07-12
I'm adding this reply after the problem has been solved because the subject line for this thread closely fits a slightly different problem I had with a wubi installation on a netbook and I want to be able to google this up later.  I had previously added a real root as super user so I don't need sudo.

My problem was that I accidently inserted a typo into fstab (i.e., an unrecognized option) which had the effect of throwing the entire root directory into read-only mode, such that I could not edit fstab to correct it.  In that case Ubuntu offers you a command line so you can log in as root, which I did.  Long story short, you don't need a recovery disk or usb stick, just do the following, as root.  If you don't have a root (super user), maybe sudo works I don't know.

First find out which device Linux thinks has the root directory (i.e., where is the wubi file):

    # fdisk -l

where l is a lower case L, not the number one. From this I could deduce it's /dev/sda3. Next choose 2 existing mount points (e.g., /mnt and /media) because you can't create any because everything's read-only. Then execute 2 mount commands, for instance, 

     # mount /dev/sda3  /media
     # mount -o loop,rw  /media/ubuntu/disks/root.disk  /mnt

Now you can go to /mnt/etc/fstab and edit it with vi!  Linux/wubi evidently lets you mount something read-write within a file system that's otherwise read-only.

---

