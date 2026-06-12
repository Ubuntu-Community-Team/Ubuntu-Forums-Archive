---
title: "initramfs busybox issues + cannot mount HD"
date: 2010-12-21
forum: General Help
---

### Post by fiyer on 2010-12-21
The issue started with a reboot after installing an upgrade package in Lucid Lynx. I was getting the initramfs errors. I did a search, found some old threads from 2008, the options listed didn't work/were not accessible. Several posters suggested changing ahci to RAID in the bios, and I didn't see an option like that when I went into it.

I've pretty much given up on accessing the harddrive through a regular boot now.  So I tried to access the harddrive with a USB version of Ubuntu.  That's where things get weird.  I have 2 internal harddrives. The old one, which is set up as a slave to the one I want to access, works fine. Instantly mounts.  The one I want to access refuses to mount. When I try to get it to mount I get the error:
**Dbus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending**

I don't mind if I have to do a fresh install over this since something is obviously very wrong, but there are a few file folders that I did not yet back up!  Any ideas on how I can access them?

I was thinking I could try to install Meerkat in a separate partition onto the uncooperative HD and see if I could read the files from the Lynx install. Would that work? Other thoughts?

---

### Post by ronparent on 2010-12-21
It should work. I've had up to four test partitions on a raid array and have had no difficulty accessing them other booted partitions to copy data.

---

### Post by fiyer on 2010-12-22
There's definitely something out of the ordinary going on.  The HD is only 5 months old, and supposedly is in good health based on what the Disk Utility said earlier today (obviously the reality is that it is dying). I did try installing from the CD and the USB onto the HD in question, and it never got passed the "hit continue" stage...

I had been able to view the fact that the HD existed via the livecd and usb  this morning, and now it is as if there is no harddrive there. 

I was looking at using testdisk or gddrescue, but that's not going to work if I can't even view the hd.  I've gone from not being able to mount it, to nothing even acknowledging that it is there.  I tried mounting from the Terminal, and it basically says there is no such thing to mount.

If I try to boot the harddrive, I get the initramfs style command prompt.  I found the wiki list of commands to use in initramfs but I didn't find anything that was step by step to make sure I get it right. If I could just figure out the right directions to access and copy the photo folder in the home directory I'd be happy. 

Any ideas? Thanks.

---

### Post by fiyer on 2010-12-23
Update: I am in the process of recovering the data.

What I did was: 
* boot from the sysrecoverycd
* shrink the partition with Gparted  (it was a 1TB harddrive and I didn't have an external so large, but less than 200GB was in use)* This took about an hour!*
* copied the partition to an external harddrive *This took about 3.5 hrs!*
* tried to run photorec from the CD, but was having trouble designating the right directory, so I installed testdisk and phororec onto a different computer and it is now happily recovering the photos and documents from the copy of the partition.

---

