---
title: "USB install not working"
date: 2010-12-25
forum: General Help
---

### Post by cc11rocks on 2010-12-25
Hello everyone! Oh, and a merry Christmas too.  I am new to the Ubuntu community and have run into a problem.  If you could help me that would be great.
So anyway my live USB (persistent 3GB; total space 4GB) is getting "stuck" at the "loading section".  It has never done this before.  The "loading section" is where it says Ubuntu and there are 4 or 5 "dots" underneath.  It just keeps going from white across to red/orange/whatever.  I left it for hours (not sure exactly how long) and it was still stuck at that sequence.  If you could help me, that would be great.  It is Ubuntu 10.04.  I do not want to format & reinstall everything because i got all my settings saved on there with all my programs and settings saved.  Plus 4-6 hours of updates (bad internet connection).  I don't remember changing anything before I shut down.  Approximate start-up time is 2 min. with persistence and 30 seconds without (before i did the persistence option i did regular).  Approximate shut down time is 1 minute with persistence and 5 seconds without.  When I downloaded the Persistence Ubuntu .iso and everything else, I formatted it.  I am running everything on a netbook, Asus EEE PC 1005 HAB if it helps.  I have Windows 7 Starter installed, too.  I am using it right now and Win 7 Starter has not been affected.  If you could help me that would be great.
Thanks and Merry Christmas,
cc11rocks

---

### Post by C.S.Cameron on 2010-12-25
There should be a warning in huge red letters saying:

DO NOT TRY TO UPDATE A PERSISTENT UBUNTU INSTALL.

It seems like it is working, but quickly fills the casper-rw persistence file.
Once this file is full you can no longer boot the drive.

Your only hope is to plug the drive into a machine running Ubuntu, mount casper-rw, and then some delete stuff off it, 
Like in var/cache/apt/archives.
Once you get it working try using computer janitor.

To mount casper-rw see:

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

---

### Post by cc11rocks on 2010-12-25
Thank you so much.  I will just reformat everything, reinstall ubuntu on my flash drive(ubuntu 10.10 this time), then make the persistent file using the terminal.  I am off for another week (from school) so I will just reinstall all the updates.  Thank you so much. :)
With much thanks,
cc11rocks

---

### Post by cc11rocks on 2010-12-27
[QUOTE=C.S.Cameron][QUOTE=cc11rocks][QUOTE=C.S.Cameron][QUOTE=cc11rocks]Hey!  I tried doing this but I couldn't get it to work.  What i tried was to boot from the USB drive and do the steps provided.  Is there any way to do this from windows?
Thanks,
cc11rocks[/QUOTE]

Sorry, what are you trying to do? Mount casper-rw?

You can not mount casper-rw if it is being used.
Try booting the live CD, then plug in Flash drive, then mount casper.[/QUOTE]
I am using the USB drive as a "live CD".[/QUOTE]

You can not mount casper-rw if you are booting the drive it is on. It gets locked.
Do you have a second USB you could use to boot from and use to mount casper-rw on the first drive? 
Or another computer running Ubuntu?

Windows will not open casper-rw.[/QUOTE]
This is what we sent back and forth.  I am posting this for knowledge of the Ubuntu community.

---

### Post by cc11rocks on 2010-12-27
It is still not working.  I installed Ubuntu 10.10 Desktop on my two 4GB flash drives.  I then booted from one of them.  I then plugged in my other flash drive.  It automatically mounted.  I then did this:
```

cd /media/PENDRIVE
sudo mount -o loop casper-rw /media/casper/
casper-rw: no such file or directory
sudo mount -o loop casper -rw /media/casper/
/media/PENDRIVE/casper: Is a directory

```
I also tried:
```

cd /
cd cdrom
sudo mount -o loop casper-rw /media/casper/
casper-rw: no such file or directory
sudo mount -o loop casper -rw /media/casper/
/cdrom/casper: Is a directory

```
I have looked on the internet and cannot figure out how to "fix" this.  If you could help me I would be very appreciative.
Thanks and Happy New year,
cc11rocks

---

### Post by cc11rocks on 2010-12-27
Bump-Please help

---

### Post by cc11rocks on 2011-01-06
Bumpity boom!

---

### Post by efflandt on 2011-01-06
If you have 2 live isos on USB, how do you keep track of which is which, did you give the FAT32 partition on them different labels?  Did you create either or both of them with persistent data?  In other words does either one have a casper-rw file on it (which is actually an ext2 filesystem within the file)?

From the error messages, it sounds like casper-rw you are attempting to loop mount does not exist.  Do an **ls** on the FAT32 partition (or look at it from Windows) to see if there is a casper-rw.

Another method I used for Natty (which is under development and does not properly use a casper-rw file) was to use gparted to create a 1 GB FAT32 partition, and partitioned the rest as ext2 (no label yet).  I used Startup Disk Creator to make the live iso in the FAT32 partition with minimal 128 mb persistence, then deleted casper-rw file, then used gparted to "label" the ext2 partition as "casper-rw".  Then when you boot it, it would automatically use the casper-rw "partition" for persistent data.  And if you want to read the persistent data from another Linux system, the casper-rw partition would usually automount when you plug in that USB (no loop mounting necessary when it is a regular partition).

You can add programs to a live iso on USB with persistent data.  But **do NOT try to do updates or add video drivers**, because initial boot is fixed, and things like kernel updates or video drivers will not work.

---

### Post by C.S.Cameron on 2011-01-07
Sorry for the late response, I was traveling.

Since you are using two pendrives, in order to make sure you have the right path to casper-rw, find casper-rw in Nautilus, right click it and copy.
Paste this into terminal, then delete the //file stuff.

---

