---
title: "Win 7 Ubuntu 10. Cant Boot either 1"
date: 2011-06-05
forum: General Help
---

### Post by avinstall on 2011-06-05
I ran the boot_info_script.sh and here are the results. However, I had an error when I ran it. I posted that message at the beginning of my resulats text.
 
Any helpp will be greatly appreciated
 
Thanks, Lloyd

---

### Post by garvinrick4 on 2011-06-05
You have a dynamic disk instead of basic. When did you change that? 
I do not even believe Linux will work inside a dynamic disk, when did you install WUBI version of UBuntu?

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 [COLOR=Red]SFS[/COLOR]
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   834,809,855   834,400,256  42 SFS
/dev/sda4         834,809,856   976,771,119   141,961,264  42 SFS

---

### Post by avinstall on 2011-06-05
As far as I can remember Ubuntu said it could change the size of my windows partition to give me room to install ubuntu. As far as it being dynamic, is that some thing I would have had to change?

---

### Post by garvinrick4 on 2011-06-06
> **avinstall said:**
> As far as I can remember Ubuntu said it could change the size of my windows partition to give me room to install ubuntu. As far as it being dynamic, is that some thing I would have had to change?
Yes go back to basic.

---

### Post by Mark Phelps on 2011-06-06
> **avinstall said:**
> As far as I can remember Ubuntu said it could change the size of my windows partition to give me room to install ubuntu.

Big mistake -- letting the Ubuntu installer mess with your MS Windows partitions.

Looks like it FORCED the creation of another partition, which unfortunately, in Win7 (which is what I'm guessing you had in place) can then FORCE the conversion of Basic disks to Dynamic disks.

You will NOT be able to convert back to Basic disks if you have more than 4 primary partitions on the drive -- MS Windows will not let you do the conversion.  You will have to remove any extra partitions, first.

---

### Post by Rubi1200 on 2011-06-06
I am surprised you were able to install Wubi at all!!!

As garvinrick4 pointed out, dynamic disks and Linux do not go well together.

This is the first time I have heard of a Wubi install on a dynamic disk.

Could you please provide some more detailed information about the installation process and whether, to the best of your knowledge, the disks were dynamic before you installed with Wubi.

---

### Post by avinstall on 2011-06-06
The disk were not dynamic to begin with. What kills me is the dual boot setup has been working for the last 3 weeks. 
I guess, based on what I'm hearing I will start the tedious process of saving my files and reloading Windows 7, unless the are any magical suggestions.
 
Thanks, Lloyd

---

### Post by Rubi1200 on 2011-06-06
Read the posts here by oldfred and srs5694 (they really know their stuff), but also pay attention to the caveats:
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)

In any event, make full backups before you do anything!

---

### Post by bcbc on 2011-06-06
Wubi doesn't create or modify partitions. It's not possible that wubi could create a partition, and not possible that Windows would decide to convert to dynamic on the fly.

More likely is that you were unaware that you had dynamic partitions. Ubuntu is blissfully unaware of dynamic partitions and will just refer to the partition table for information. Which can be disastrous if you are mounting and writing information to the windows partitions (including /host). The actual Wubi root.disk will be wholly contained within a single partition so shouldn't result in problems if you just used the virtual disk for storage.

The only thing that prevents installing Wubi to dynamic disks seems to be bcdedit (in other words Windows) that rejects adding bcd entries that refer to dynamic disks that are not in the partition table.

That's my theory. I haven't tested dynamic disks with Wubi (nor do I intend to). But I think a bug should probably be raised for Wubi (and Ubiquity) to detect dynamic partitions and prevent reject the installation attempt with errors.

---

### Post by Rubi1200 on 2011-06-06
I wonder why you are unable to boot Windows?

According to the script results, sda1 is not mounting. Is that the system recovery partition?

Yet, the boot flag is on sda2, which would suggest that you should still be able to boot?

Do you have recovery disks for Windows?

Sorry for so many questions, but we want to help you here.

Please try and remember as much as possible the sequence of events and let us know so we can try and figure this out.

Thanks.

---

