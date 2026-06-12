---
title: "Dual-Booting on my laptop, i need help with partitions..."
date: 2011-06-21
forum: General Help
---

### Post by TacticalApe on 2011-06-21
I just got this laptop, and since I love ubuntu I want to dual boot it like I have on my desktop. But my disk already has 4 partitions, and from what I understand that's as much as I can have. I obviously need to keep the C: 
partition, but what about the other 3? Here's a screenshot of the partitions: 

[IMG]http://img811.imageshack.us/img811/2816/parions.png[/IMG] 

Once I get this figured out I can do the rest.

---

### Post by sidzen on 2011-06-21
Download EasyBCD at [www.neosmart.com]("http://www.neosmart.com") along with [Win7 recovery Disk]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")
I'd then create a recovery/rescue CD using windows, ghost everthing as-is and burn it to DVD; shrink C:\ a little, if desired;
Then use [gparted]("http://sourceforge.net/projects/gparted/") to eliminate the D:\ and F:\ drives, formatting to ext2 before partitioning; partition a root (/) of 11-15GB depending on distro and use Extended partiton for remainder or almost all of it; make logical partitions of /home and swap (at least) in the extended partition
install Easy BCD (may have to format the small System partition, use Win7 Recovery and EasyBCD) to use Win boot mgr to choose OS
I only did this once on a Lenovo --  HP could cause you problems
Best wishes!

---

### Post by wildmanne39 on 2011-06-21
Hi, I am going to give you a link on how to resize partitions from windows, scroll down the page a little ways and you will see pictures of how to do it. Also you should use grub as your boot manager it works really well.
The Hedge shows  graphically how to delete & create partitions in windows 

[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by TacticalApe on 2011-06-21
> **sidzen said:**
> Download EasyBCD at [www.neosmart.com]("http://www.neosmart.com") along with [Win7 recovery Disk]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")
I'd then create a recovery/rescue CD using windows, ghost everthing as-is and burn it to DVD; shrink C:\ a little, if desired;
Then use [gparted]("http://sourceforge.net/projects/gparted/") to eliminate the D:\ and F:\ drives, formatting to ext2 before partitioning; partition a root (/) of 11-15GB depending on distro and use Extended partiton for remainder or almost all of it; make logical partitions of /home and swap (at least) in the extended partition
install Easy BCD (may have to format the small System partition, use Win7 Recovery and EasyBCD) to use Win boot mgr to choose OS
I only did this once on a Lenovo --  HP could cause you problems
Best wishes!

I followed the link to the recovery disc download, and it gives me the link to download a vista disc.... I have windows 7. I did find [_this tutorial_]("http://forums.techarena.in/guides-tutorials/1114725.htm") on how to  make a disc... Would that work? And also when I do make the disc, do I go ahead and delete the HP_TOOLS partition and the RECOVERY partition?

---

### Post by sidzen on 2011-06-21
How do you intend to ghost everthing as-is and burn it to DVD?

This needs to be done as a precaution before shrinking the C:\ and deleting the D:\ and HP_TOOLS  partitions.  wildemanne39 has provided link to instructions on how to shrink the C:\ (by about half should be okay).

yes, i see neosmart has deleted the link to its Win7 recovery, so that from techarena.in should be fine, i would think.

If you use about 200GB for linux, a Primary partition of 15GBfor *root (/)* formatted to ext4 file system and an Extended partition of 100GB would allow a */home* logical partition of ~98GB and a *swap* of 2GB.  Alternatively, should burning DVDs be a priority, the / could be made smaller and a */tmp* partition of 4.6 to 5GB added as a Logical partition within the Extended, in addition to /home and swap.  

NOTE:  some of the hard drive within the Extended partition could be left *unallocated* to allow for future options

Have fun!

---

### Post by TacticalApe on 2011-06-22
What do you mean by ghosting everything as-is? Do you mean like copying everything to a cd or something?

---

### Post by gizmo720 on 2011-06-22
Try booting into a livecd and running gparted. On my computer one of the 'Primary' partitions windows saw was actually a logical one. If that is the case boot back into windows, and use its partitioner (Right-click My computer and select manage, in the left pane, go to Storage>Disk Management) to shrink the C: drive. Using gparted for this (and most other programs) Will make windows unbootable.

Boot back into the livecd and load gparted again. You can now extend the logical partion into the free space, and make as many partions as you want in it.

If none of them are logical, this won't work.
If windows complains about unmovable files, disable hibernation and pagefiles (Google it), then reboot and try again. If that doesn't work you can try disabling system restore, after that, you are out of luck.

---

### Post by sidzen on 2011-06-23
see this link -- [PING (Partimage Is Not Ghost)]("http://ping.windowsdream.com/") -- it may help.

---

