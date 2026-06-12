---
title: "hard disk capacity missing?"
date: 2011-07-22
forum: General Help
---

### Post by sumithar on 2011-07-22
I see a mismatch in available disk space b/w Disk Usage Analyzer and the Folder view.  One says 18 GB, the other 13GB- please see attachment.

Any ideas?

Thanks

---

### Post by Frogs Hair on 2011-07-22
I think because a minimum of 4.6 to 5 GB is required to run the OS , but I don't I know why the space is accounted for in one application and not the other.

---

### Post by galvatron408 on 2011-07-22
i don't trust either one. i did what you did and got different results as well. then, i ran a "df -h" and got something else. 

I rather trust df.

---

### Post by sumithar on 2011-07-22
I have a 10GB partition for the OS, it's an 80GB HD, as you see the utility is only showing 70GB

---

### Post by psusi on 2011-07-22
What does df show?

---

### Post by Frogs Hair on 2011-07-22
To check disk space from the command line use the following .```
df
``` To check file system usage.```
df -h
```

---

### Post by mcduck on 2011-07-22
> **sumithar said:**
> I see a mismatch in available disk space b/w Disk Usage Analyzer and the Folder view.  One says 18 GB, the other 13GB- please see attachment.

Any ideas?

Thanks

5% of the space on Ext file systems is by default reserved to root user only, to prevent normal users from filling the file system to the point where the system can't create necessary files to boot. The reserved amount can be changed (or even set to 0), but you shouldn't touch that on your root partition, and in the end the performance of Ext filesystems starts to degrade quickly due to fragmentation if the disk gets too full so you'd never actually want to fill the drive more than 95% anyway.

On the other hand your file manager is running as your own user (obviously), so it's only showing the space that's available for *that user*.

Also the Disk Usage Analyzer isn't really a tool for checking how much space you have used/available on a certain partition, but rather for analyzing where the space is being used. You *can* use it to check the used/available space, but to do that you need to set it to scan only a certain file system and exclude mounted partitions etc, otherwise it will just show you a combined total space from all mounted partitions, removable drives etc.

If you want to actually check the used/available space on different partitions, then running "df -h" in a terminal is the best tool.

(so all the tools give you correct values, it's just that they are correct value for different things. :D )

---

### Post by mcduck on 2011-07-22
> **sumithar said:**
> I have a 10GB partition for the OS, it's an 80GB HD, as you see the utility is only showing 70GB

Keep in mind that hard drive manufacturers present the disk sizes using a different unit than what the computer's actually use, and different programs aren't always using the correct names when presenting the values to you.

Your computer uses multiplier of 1024 for every K, M etc, while hard drive manufacturers count them using 1000 as multiplier. While the current standard would be refer them as KiB, MiB etc when using 1024 as multiplier, and KB, MB etc when using 1000, it's quite common that programs just use the KB, MB and GB regardless of which multiplier they are counting with.

So if you had a computer with a 1 GB (actually 1 GiB) of RAM, and a 1GB hard drive, you couldn't write all the data from RAM to the hard drive. It would be too small (only 0,93 GiB).

(I wouldn't blame the program developers, though, as they are just using the same units they have always used, while the standard was changed some time ago. The old way was correct from technical point of view, computers operating in binary and 1024 being the closest sensible value to 1000 to present by a binary system. On the other hand the new way is correct from the SI standard's naming scheme's point of view, and is also consistent with the way hard drive manufacturers like to market their drives)

---

### Post by sumithar on 2011-07-23
Thanks everyone- df and its variants do echo what's shown in the "Home Folder" view.
Disk usage analyzer shows what is in the boot partition plus the home partition but leaves out the 10GiB that's in the "Extended" and "Swap Space" partitions.
See attached

Good information from  you all especially the GB vs GiB distinction.

Thanks again

---

