---
title: "gparted shrink win7 partition no boot"
date: 2011-08-14
forum: General Help
---

### Post by psycho5 on 2011-08-14
Hi, I tried to fix my win7 boot after shrinking the partition 20gb from the left (empty space was around 200gb in it). Now I am in windows 7 recovery..

I did the following
chkdsk c: /r  returned no errors 

In C:\ 

bootrec /FixMbr  no errors...successful

bootrec /Fixboot  The volume does not contain a recognized file system. Please make sure that all the required file system drivers are loaded and that the volume is not corrupted. 

bootrec /rebuildbcd    It finds the windows installation, but after hitting Y to add to the boot list, I get the same error: The volume does not contain a recognized file system. Please make sure that all the required file system drivers are loaded and that the volume is not corrupted. 

When I try to boot into windows it says File: \Boot\BCD Status: 0xc000000f Info: An error occurred while attempting to read the boot configuration data

---

### Post by psycho5 on 2011-08-14
I read from Gparted FQA that the preceeding size in bytes should be 0 when resizing a windows patition, but I think I left it at 1. I don't recall changing any values preceeding the partition.

---

### Post by psycho5 on 2011-08-14
I followed all options here:

[http://support.microsoft.com/kb/927391](http://support.microsoft.com/kb/927391) 

but I get : The system cannot find the file specified

or the boot configuration data store could not be opened. 


guess i gotta reinstall? Is there a way around that?

---

### Post by spiky001 on 2011-08-14
load windows 1st. I normally make a partition for windows 1st. Then leave rest unallocated then install ubuntu to unallocated space

---

### Post by Mark Phelps on 2011-08-14
> **psycho5 said:**
> guess i gotta reinstall? Is there a way around that?

You could try just doing the Repair Install three times, instead of entering the commands yourself.  Sometimes, that works -- it just takes a long time to do the reboots.

And NEXT time, do NOT use GParted to mess with Win7 partitions.  Use the Win7 Disk Management tool, instead.

And, if you want to do things that the Win7 utility doesn't support -- use MS Windows tools, not Linux tools.  You can download free versions of Partition Wizard and EASEUS Partition Master that will do partitioning.

---

### Post by psycho5 on 2011-08-14
> **Mark Phelps said:**
> You could try just doing the Repair Install three times, instead of entering the commands yourself.  Sometimes, that works -- it just takes a long time to do the reboots.

And NEXT time, do NOT use GParted to mess with Win7 partitions.  Use the Win7 Disk Management tool, instead.

And, if you want to do things that the Win7 utility doesn't support -- use MS Windows tools, not Linux tools.  You can download free versions of Partition Wizard and EASEUS Partition Master that will do partitioning.

Repair install... haven't tried that. are you sure it's repair install or you're talking about the startup repair tool?

---

### Post by psycho5 on 2011-08-14
If you're talking about Startup Repair, it fails it says Startup repair can't fix the errors on the disk. In details it shows that OS = (blank) or unknown instead of windows 7 and the location field is also blank.

---

### Post by YesWeCan on 2011-08-14
Would you post sudo sfdisk -luS?
Windows needs to have its boot flag set before it will repair the boot. This could be the issue.

---

### Post by psycho5 on 2011-08-14
> **YesWeCan said:**
> Would you post sudo sfdisk -luS?
Windows needs to have its boot flag set before it will repair the boot. This could be the issue.

I would do that... except I already went ahead and backuped my data and formatted it.. lol i was just getting to inconvinienced with the whole situation.

---

