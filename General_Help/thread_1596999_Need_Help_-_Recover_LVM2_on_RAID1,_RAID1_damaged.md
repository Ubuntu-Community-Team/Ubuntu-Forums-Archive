---
title: "Need Help - Recover LVM2 on RAID1, RAID1 damaged"
date: 2010-10-14
forum: General Help
---

### Post by cdebuhr on 2010-10-14
**Summary of The Problem:**
I have a RAID1 (/dev/md0 consisting of /dev/sdc4 and /dev/sdd4) serving as physical storage for an LVM2 volume group (/dev/VG1 on /dev/md0p0) containing two logical volumes, including one mounted on /home.  I accidentally clobbered the RAID1, and it now shows up as being completely unallocated with no partition table.  The RAID metadata also shows the array as being recently created, so I'm assuming that got clobbered as well.

I've made no attempt to recreate partitions, file systems, etc., or anything else that would write to the disks, and the "clobbering" was pretty much instantaneous, so I'm assuming the LVM Vgroup is still in there and, hopefully, intact.

I tweaked fstab to use an old backup copy my  /home partition to get me back up and running, but theres quite a bit of data I'd like to get back, if possible.  I'd like to do one of two things, either 1) get the old RAID1 going again so I can see the Vgroup and get my data, or 2) forget the RAID, and directly access the Vgroup in either of /dev/sdc4 or /dev/sdd4.

Please Help!!

**Details:**
I'm currently running Ubuntu 10.10 x64 (upgraded from 10.04). I've been playing around a lot with RAID and LVM, mostly as a learning exercise.  As a result my file system is **way** more complicated than it should be for a standalone desktop system.  My pre-disaster storage configuration was:

/dev/sda1      Reserved
/dev/sda2      backup copy of /home (now mounted on /home)
/dev/sda5      /
/dev/sda6      swap
/dev/sda7      LVM2 phyical volume (contains LVM2 Vgroup VG0)

/dev/sdb1      /mnt/scratch

/dev/sdc1      Reserved
/dev/sdc2      swap
/dev/sdc3      Reserved
/dev/sdc4      RAID1 Component (part of /dev/md0)

/dev/sdd1      Reserved
/dev/sdd2      swap
/dev/sdd3      Reserved
/dev/sdd4      RAID1 Component (part of /dev/md0)

/dev/md0p0     LVM2 physical volume (contains LVM2 Vgroup VG1, currently inaccessile)

/dev/VG0/OPT   /opt
/dev/VG0/TMP   /tmp
/dev/VG0/USR   /usr
/dev/VG0/VAR   /var
/dev/VG1/DATA  /mnt/user.data (currently inaccessible)
/dev/VG1/HOME  /home (currently inaccessible)

Like I said, way too complicated, but I'm relatively new to the Linux world, and this is how I've been teaching myself about the  file system.  I've also been doing LOTS of installing and uninstalling from the repositories, so the system is getting pretty messy anyway.

I was planning a clean reinstall to 10.10 sometime soon, and, aware that the normal desktop installer doesn't do RAID or LVM, was looking at the alternate installer.  I only intended to get as far as the partitioning tool to have a look at how it handled RAID and LVM.  I could see all my partitions and the LVM2 volumes in VG0 (hosted on /dev/sda7, i.e., non-RAID), but there was no sign of the RAID1 or the volumes in VG1.  So I selected the "Configure software RAID" option.  This must be how you activate an existing RAID set, right?  I then went ahead through the options, selected /dev/sdc4 and /dev/sdd4, and committed changes.  I'm pretty sure this was the fatal action.  After this point, I could see the RAID1, but there was still no sign of my missing LVM2 volumes.

After poking around a bit more (I did not attempt to create or attach to any other existing LVM2 physical volume).  I rebooted the system, only to get a volume mounting error on the home partition.  I'm used to getting these mount errors when I'm tinkering - a few minutes in nano with the right conf files, and maybe a tweak to /etc/fstab and I'm good to go.  This time, however, it was clear that I had done "Something Bad" to my RAID1.  The good part is that whatever I did, it happened quickly, and with relatively little disk activity, so I'm pretty sure that my LVM2 Vgroup should still be in there, somewhere.

So, after all that, can anyone tell me what, exactly, I did? I think what I did was to destructively create a new RAID1 using components from the existing array, but I don't think much actual data was written, and I've been careful not to do anything that would commit new writes to the partitions in question, so I'm hopeful that someone here can help me get my data back.

And by the way, no, I don't have a recent back up.  I know, I know - I'm an idiot!!

Thanks very much!!

Chris

---

