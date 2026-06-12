---
title: "Partitioning Help"
date: 2010-02-06
forum: General Help
---

### Post by paopao on 2010-02-06
Hi.  I don't know much about partitioning, so please kindly go into more detail about suggestions (e.g., posting commands) instead of vague responses that would probably be useful to someone with more experience.  Thank you.   

I recently built a computer and installed Ubuntu 9.10 server edition on it.  I used six hard drives in a RAID6 configuration.  That turned out to be a lot easier than I expected and this [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) was quite useful.  However, I wanted to test my ability to recover from failed drives before I would entrust the location with all my data. 

So, first any good links (that slipped passed Google searches) about rebuilding RAID arrays would be nice, but not the point of this thread (yet).  What happened is that I wanted to simulated a hard drive failure, so I booted the system using a LiveCD and deleted the partition table from one of the drives.  When I reboot, it stalls on detecting that RAID array and so I escape into shell and start the RAID again, albeit degraded.  Rebooting again is fine, but of course with the degraded array.  Using an m5sum checksum I verified that the data is still the same. 

However, my issue is getting the partition table back *exactly* like it was before.  For testing purposes, I only created the RAID6 array using 200MB (the size I said for the ubuntu server edition installer) for each drive.  But if I used Gparted on LiveCD, I cannot get the partition to be 200MB.  Fdisk won't work because the hard drives have GPT.  I installed ubiquity to use partman, but there again I cannot get the sizes to be exactly the same - also in the original installation, I was able to tell the partitions that they would be used for RAID, I'm not sure how to format these partitions (if at all) for when I would have them rejoin the RAID array).  I'm not sure what other partition programs there are because frankly, most people only deal with the partition in the installer and formating their flash drives. 

I'm thinking an easy solution would be if I could *copy* the exact partition table from one of the five working drives to the new drive.  All six hard drives are exactly the same, so there's no issue there.  I tried searching for copying partition tables, but nothing was really illuminating.

---

### Post by louieb on 2010-02-06
I'm surprised the **dd** or **sfdisk** command did not come up in your search.  
Both will work with the old standby msdos partition table. 
Maybe they do not work with a GPT partition table either - never used GPT so would not know.   

You can save the partition table in its native binary format with the command
     
     ```
sudo dd if=/dev/sdc of=PT_sdc.img bs=1 count=66 skip=446 
```
and you can restore the partition table with the command
     
     ```
sudo dd of=/dev/sdc if=PT_sdc.img bs=1 count=66 skip=446 
```

 Another program that can make and restore an exact copy or your partition table is sfdisk.
save
```
sudo sfdisk -d /dev/sdc > PT.txt
```restore ```

sudo sfdisk --force -I PT.txt /dev/sdc
```

---

### Post by paopao on 2010-02-06
Thanks for the reply. 

The issue is with GPT.  According to my quick research on Wikipedia, there are records of the partition table at the beginning and end of the disk (and bigger than whatever the older version of partition tables is called), so the *dd* command wouldn't work. 

I tried sfdisk and got the warning message: 
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util sfdisk doesn't support GPT. Use GNU Parted. 

```Ignoring that, I tried to restore it anyway, but got the error message: 
```
sfdisk: partition restore file has wrong size - not restoring 
```To clarify, when I use Gparted (LiveCD) there is an option to copy a partition and paste it (although only for the ext4 formatted ones (2 out of 6 of the drives have unknown formatting - my guess is those 2 are the parity drives).  I did a copy and paste and still the size of the partition is smaller (no idea why).  In fact, it's quite messed up.  /dev/sdd is OK, in Gparted it lists sizes as MiB.  /dev/sdd1 is 190.74 MiB with 42.85 MiB used and 147.89 MiB unused.  When I copy it, /dev/sdf1 is 188.26 MiB (smaller) with 42.85 MiB used (same size, at least that's good) and 148.15 MiB unused (larger).  Seriously, how could the partition be smaller when the total of used and unused is greater (190 MiB)?! 

A guess, on the working drives, the first partition starts at sector 34 (why 34?), but when I copy, I can ask where I want the partition to start in terms of MiB, too larger to account for 34 sectors (34*512 bytes = 0.016 MiB). 

At least I'm dealing with these issues *now* when data is not a concern as opposed to later when I'm doing a recovery for real.

---

### Post by oldfred on 2010-02-06
I do not know raid or GPT but have been reading up on GPT since it seems to be the future if you want to partition any drive over 2TB. If you have GPT all the tools you use have to be GPT tools, many tools are older and just for MBR like fdisk. Most of the older tools have been updated to recognize GPT and not do anything to damage them.

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by paopao on 2010-02-06
I found a solution to my problem, albeit not my original idea.

Instead of being able to copy the partition table from one disk to another, I did find a tool that had find control over the exact size of the partitions down to the byte (which probably rounded to the nearest sector).  The tool was called <b>parted</b> and it handles GPT.  As a note, sizes need to end with a unit (e.g,. 17408B).

---

### Post by paopao on 2010-02-10
Some additional information.

For my computer, I have a RAID1 for the OS with the "small" 750GB hard drives, so they have the msdos partition table, where the sfdisk command works.  However, when I used the suggested restoring command, I got the same filesize mismatch error.

I found a website with a better (and working) partition table restoring command:

[http://prefetch.net/blog/index.php/2009/08/06/backing-up-and-restoring-partition-tables-on-linux-hosts/](http://prefetch.net/blog/index.php/2009/08/06/backing-up-and-restoring-partition-tables-on-linux-hosts/)

In short, you can use the first to save and the second to restore:
```
sudo sfdisk -d /dev/sdc > PT.txt
sudo sfdisk /dev/sdc < PT.txt
```
**Be extremely careful since the direction of the arrow keys can very easily destroy your partition table which would be very bad.**

---

