---
title: "How to retreive data on BSOD hard drive?"
date: 2011-01-27
forum: General Help
---

### Post by jimhokie on 2011-01-27
My daughter's netbook, an Acer Aspiron One, running XP with a 160GB hard drive get's a "unmountable volume" blue screen error.  I was unable to boot from a Dell XP disc I had for another computer, but it will boot up with the Ubuntu live cd.  But when I try to access the hard drive from there, I get this message: 

"Unable to mount location
Error mounting: mount exited with exit code 13:
ntfs_attrpread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $BITMAP: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware.  In this case run chkdks/f on
Windows
then reboot into Windows twice.  The usage of the /F 
parameter is very
important!  If the device is a SoftRAID/FakeRAID then first
activate
it and mount a different device under the /dev/mapper/
directory, (e.g.
/dev/mapper/nvidia_eahaabcc1).  Please see the 'dmraid'
documentation
for more details."

That is all greek to me.  I tried to follow some directions I found for how to force mount the volume, but have been unsuccessful, probably because I'm not savvy enough to understand the instructions accurately enough.  

I also downloaded SeaTools for DOS and ran the long test that found 1 error..."bad sector found".  I guess since the SeaTools program was able to scan the drive, it hasn't totally failed, so is there still hope I can access the hard drive?  My daughter has all her pictures and music on it.  She has learned her lesson about backing up anything she doesn't mind losing, but I'm trying to minimize the cost of that lesson for her!

Any thoughts or suggestions for how to access the drive based on the above will be greatly appreciated!

---

### Post by CharlesA on 2011-01-28
Basically the partition is marked as "dirty" and needs to have chkdsk run on it.

You would have to get Windows loaded on the drive, or pull it out of the netbook (not sure if that's possible) and run chkdsk on it from another machine.

If SeaTools has found bad sectors, then the drive is more then likely toast.

---

### Post by rcayea on 2011-01-28
I would suggest Recuva if you can hook the hard drive up to a windows machine. 

Or, you might want to look at this:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by darkhelmetchris on 2011-01-28
I will offer my 2 cents...

When it comes to data recovery, I am a BIG believer in using some caution.  I want to suggest that applying any kind of write-to-drive changes on a potentially failing drive might be a bad idea, because you might ruin your "last chance".  Using a "read only" method of data recovery is generally a good idea.  I would like to suggest that you try to clone the bad drive to a known-good drive, and then try potential fixes (like chkdsk) on the copy.  You can use ddrescue to do this sort of thing, and it will do a pretty good job of retrieving the good data.  ddrescue (like dd) will clone your drive sector by sector, regardless of the type of partition you have, and it will attempt to recover bad data, hopefully leaving you with the "best of" what it could recover.  Running ddrescue might take a long time if your drive is in bad shape - it's okay if it takes a long time; I've had an 80GB drive take 2 days to clone when it was attempting to recover many bad sectors.

To accomplish this idea, start up with your LiveCD; don't bother to try to mount the partition, you will be cloning directly by sector.  Open up your Synaptic Package Manager and enable the "universe" set (Settings, Repositories) then install ddrescue either here in Synaptic, or at the command line like this:
```
sudo apt-get install gddrescue
```
Then connect a known-good drive via USB or eSata, or by what ever method your drive requries.  Identify your drives, GParted is good for that - you can turn on the device information (view, Device Information) so you can see which drive is which one.  Clone your hard disk to the good one like this:
```
sudo ddrescue <source-drive> <target-drive>
(for example, if your bad disk is /dev/sda, and your new good disk is /dev/sdg then do:
sudo ddrescue /dev/sda /dev/sdg
WARNING:  make sure you have identified your drives correctly; it would be quite disappointing to clone from target-to-source by accident
```

Once you have cloned your disk, set your original source drive aside, and proceed with trying to do data recovery on the new copy.  If something goes wrong, or you make a mistake with your data recovery efforts on the new drive, you then have the option of going back to cloning again, to get a good baseline.  You wouldn't have that option if you had not made your backup with ddrescue.

I hope you have good luck.

---

