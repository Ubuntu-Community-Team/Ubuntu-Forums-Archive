---
title: "Hard disk not found from live-cd boot"
date: 2012-06-27
forum: General Help
---

### Post by 43rdTree on 2012-06-27
I am working on a computer that does not actually have Ubuntu installed, but has three partitions: one current Windows XP partition, an old (formerly virus-infected) XP partition, and a general storage partition (I don't remember the filesystem type). I was planning to wipe the disk and reinstall XP, but before I got a chance to XP started acting up, telling me that it has a problem with its Windows activation and not letting me do anything. It does boot, though. 

I booted from an Ubuntu 9.04 Live cd to copy all of the files to a portable hard disk, and at first, the internal hard disk did not show up (as in, on the surface, it might as well not have existed). After a reboot, though, it showed, and I backed up the files. After I found the Windows install disk I booted into Ubuntu again to repartition the drive, and it has again disappeared. 

Reboots do not make it show up, and I do not know what to do to access it. I also tried booting from an old 6.10 disk with the same result and then from the XP install disk, which denies that the computer has a hard disk. Still, I can boot from that hard disk, so it is clearly working. The only thought I have been able to come up with is that some how the computer isn't scanning for its hard disk when it boots from cd, though it will recognize external disks. 

I'm hoping that there is some way to manually force Ubuntu to discover the internal hard disk. I don't know much about manual mounting and so I can't judge if Ubuntu is at all aware of the disk and just not mounting it or not. 

Information that might be useful:

I tried running GParted to see if it would scan and find the disk but it says "No devices detected."

sudo fdisk -l returns nothing.

I read elsewhere to try parted -l. It returns:

"Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label"

Something exists as /dev/sda but I don't know what to do with that information.


I appreciate any suggestions.

---

### Post by quadproc on 2012-06-27
It sounds as though you have tried the usual approaches to the problem.  Could it be a hardware problem?  That would explain the described symptoms.

If you can get the program hardinfo to run (from any OS) then it might help to troubleshoot the system.

quadproc

---

### Post by 43rdTree on 2012-06-27
I'll try to test it more, but I don't think it is a hardware problem because it boots smoothly into Windows up to the login screen, so it can clearly read the drive then. Though I'm not sure what caused Windows to stop working, which is suspicious. My brother (usual first source of tech support) suggested that it's possible that parts of the disk are becoming corrupt and so it can no longer read the sections relevant to the activation. But I think (maybe wrongly) that it would take even more damage than that to make Ubuntu not able to see the disk, and that then Windows wouldn't be able to either.

---

### Post by MrNovi on 2012-06-27
My advice would be to download PartedMagic  [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php) and boot to it.  Click on Smart Control and run the most exhaustive test on your hard drive to see what it has to say about it.  

If PartedMagic can't find the drive, chances are it's dead and will require Recovery Software (if you are lucky) or a Recovery Service (if you aren't) to get your files back.

PartedMagic will also be able to backup/copy the files to another hard drive if the drive is functioning.  It's a much better option that trying a "Buntu cd  for your needs as it is designed for this type of use.

If this steps on any of the "Buntu toes, I apologize.  But to my knowledge, they don't offer any versions that have all of the capabilities in PartedMagic.

---

### Post by 43rdTree on 2012-06-27
I will try that. I'm in the comfortable position that all of the files are backed up, I just can't make the computer work. And I know that the disk isn't entirely dead because I can boot off of it, which makes Ubuntu's non-access a bit of a mystery.

---

### Post by 43rdTree on 2012-06-27
Though given that the hard disk works whenever I directly boot from it and never when I boot from cd, I wonder if it is more of an issue of something failing to initialize on boot-up than it is of the hard disk itself failing...

Also, is there some way I can make sure that it isn't being noticed at all, not somehow only partially noticed? Or does fdisk -l not returning anything confirm that?

---

### Post by MrNovi on 2012-06-27
That's one of the reasons I recommended booting with the PartedMagic disk.  It has diagnostic software that the Ubuntu Live CD doesn't.  Plus, the PartedMagic Live CD is better equipped to recognize and mount an NTFS partition than any 'Buntu based LiveCD.  That should be your first step in diagnosing the problem.  It's quite possible that it's a problem with your Ubuntu LiveCD itself. 

Another good LiveCD to use for accessing NTFS drives/partitions is Knoppix.  [http://www.knoppix.com/](http://www.knoppix.com/)  Again, it's ability to access NTFS drives/partitions is much better than any of the 'Buntu's.  NTFS is one of the Achilles Heels of any Buntu based distro, especially anything after 10.04, but the Buntu's have never been that good with NTFS, not matter how much they try to ignore it.

---

### Post by Cheesemill on 2012-06-27
Try booting from a Ubuntu 12.04 CD instead.

9.04 reached end-of-life over 18 months ago and is no longer supported so it doesn't get security updates any more as well as having old versions of software.

12.04 will have much newer versions of the NTFS software on it and is more likely to recognise your drives.
I've never had any problems accessing NTFS partitions from Ubuntu, the modern drivers are rock-solid.

---

### Post by 43rdTree on 2012-06-27
I'm burning the PartedMagic disk now. It took some work-around to set up because my router is broken and the only computer that usually connects without it is the one that isn't working. But that's taken care of. I'll let you know how the disk works in a few minutes. 

If that doesn't work out I'll try 12.04. I just didn't have a disk on hand.

---

### Post by MrNovi on 2012-06-27
> **Cheesemill said:**
> Try booting from a Ubuntu 12.04 CD instead.

9.04 reached end-of-life over 18 months ago and is no longer supported so it doesn't get security updates any more as well as having old versions of software.

12.04 will have much newer versions of the NTFS software on it and is more likely to recognise your drives.
I've never had any problems accessing NTFS partitions from Ubuntu, the modern drivers are rock-solid.


I beg to disagree.  Anything after 10.04 has terrible NTFS support

But he would be much better off with the PartedMagic or Knoppix disk for what he needs to do, especially the PartedMagic as that can actually test the disk to see if it has a physical problem.  I don't know of any 'Buntu distro that has SmartControl built in, and that's what he needs.

---

### Post by 43rdTree on 2012-06-28
So the PartedMagic disk could not detect the hard disk either. 

And I don't really think that NTFS support is an issue, given that the Windows XP installation disk (which should have pretty good NTFS support) doesn't detect it either.

I'm suspecting it's more of a BIOS problem than an OS problem given that it affects all cd boots but the hard disk is found to boot from. But I've used live cds on this computer before without this problem, so I don't know what changed. 

I was hoping there was some way of forcing Ubuntu to check for the hard disk, but I don't know of one.

---

### Post by MrNovi on 2012-06-28
Look in the bios to see if there is a setting for the SATA controller that you can change to IDE or Comparability mode.  If so, change it to that, then boot into the PartedMagic disk to see if that changes anything.  DO NOT boot into Windows if you make that change though, as that could cause problems down the road.  

The other thing to try is download whatever self booting disk utility the hard drive manufacturer has available and boot to that to test the drive.  I know Hitachi, Samsung, Seagate, and WDC all have them.  Toshiba does't, but the Hitachi one can normally test it.

---

### Post by 43rdTree on 2012-06-28
I'm not seeing any such setting. 

Though some interesting behaviour:

If it's running off of a cd and I reboot and then look at the bios options, it doesn't show the hard disk as there, and then when I quit the options (without a reboot) and try to boot, the hard disk isn't found until I restart (when it's found every time).

Or if I don't look at the bios options, it just boots from the hard disk. 
If I look at the list of boot options (cd drive, floppy drive, zip drive) after running it from cd the hard disk isn't listed, but if I tell it then to boot from defaults, it boots from the hard disk.

If it'd been running from the hard disk before the reboot to look at the bios settings, the hard disk shows up and the computer proceeds to boot from it without a problem. The boot options list the disk.

It's as if when it's been running off a cd the bios doesn't notice the hard disk until it starts to boot off it (I'm not sure how it pulls that off) but if it's been running off the hard disk then it knows it's there.

---

### Post by 43rdTree on 2012-06-28
Also I don't think any sort of cd is going to find the hard disk. The fact that two Ubuntu distros, the PartedMagic disk, and especially the Windows disk itself can't find it makes it seem to me that cds in general cannot find the disk.

---

### Post by MrNovi on 2012-06-28
That's strange behaviour indeed.  I don't remember seeing it listed, but can you provide more details on the hardware in question?  If it's a pre-built OEM system (Dell, HP, etc) could you provide the make and model number to give us something work with?  Otherwise, a rundown of the motherboard, chipset, bios rev. etc. might provide a clue.  

It's acting like booting from a CD is turning off the hard drive, or at least hiding it and I've never run across that on the thousands of systems I've worked on over the years.  But heck, anything is possible.

---

