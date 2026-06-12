---
title: "GParted Not Working on 11.04"
date: 2011-11-09
forum: General Help
---

### Post by Hosmion on 2011-11-09
Hello everyone!  I'm using GParted to go back to Windows so I can get back into my gaming life, but I'm having some problems with it.  When I select a partition, it does not allow me any options.  I can't format, can't change it at all.  

I attached a screenshot about how it doesn't have any options for me to choose from to help the issue.

Any help?

Thanks,
Lenni

---

### Post by Mark Phelps on 2011-11-09
You can't mess with any partitions that are mounted.  And, if you're running Ubuntu, you have to mount the partitions.

You will need to boot from an Ubuntu destkop PC and do the work from there.  You also might have to check the partition first and confirm that it is NOT mounted.

---

### Post by Hosmion on 2011-11-09
> **Mark Phelps said:**
> You can't mess with any partitions that are mounted.  And, if you're running Ubuntu, you have to mount the partitions.

You will need to boot from an Ubuntu destkop PC and do the work from there.  You also might have to check the partition first and confirm that it is NOT mounted.

Thank you for your reply!


I booted up and went into GParted from the boot disk, but now another issue arises:


I'm trying to change the partition into a NTFS partition.  But that is not an option in this at the moment.  What should I do to get me the NTFS option?

---

### Post by Seb71 on 2011-11-09
You can delete/format partitions when you install Windows.

---

### Post by Hosmion on 2011-11-09
> **Seb71 said:**
> You can delete/format partitions when you install Windows.
It wouldn't let me.  I did it before via GParted on the live disk, but I don't remember what I did.

---

### Post by Seb71 on 2011-11-09
What partition did you try to delete during Windows install and you could not do it? For instance, you can not delete the extended partition until you delete all the logical partitions from it. In your case, you can not delete /dev/sda2 until you delete /dev/sda5.

---

### Post by Hosmion on 2011-11-09
> **Seb71 said:**
> What partition did you try to delete during Windows install and you could not do it? For instance, you can not delete the extended partition until you delete all the logical partitions from it. In your case, you can not delete /dev/sda2 until you delete /dev/sda5.

Why would I delete an entire partition?  I just want to format it, change it to NTFS, and install Windows onto it.

---

### Post by Seb71 on 2011-11-09
> **Hosmion said:**
> Why would I delete an entire partition?
Because you said that you can not format it.

If you want to get rid of Ubuntu and install Windows, the simplest way is to erase all the partitions (after you backed up the data - if you have any data that needs to be backed up) and start from scratch during Windows install (make and format partitions as desired).

If that is not the case and you want to do something else (like dual boot), then please clarify.

---

### Post by Hosmion on 2011-11-09
> **Seb71 said:**
> Because you said that you can not format it.

If you want to get rid of Ubuntu and install Windows, the simplest way is to erase all the partitions (after you backed up the data - if you have any data that needs to be backed up) and start from scratch during Windows install (make and format partitions as desired).

If that is not the case and you want to do something else (like dual boot), then please clarify.
If I delete all of my partitions and go in to install Windows, it will still give me an option to install?  I thought when you get rid of your partitions you get rid of all of your drives and stuff.  I didn't know you could do that.

No, I don't plan on dual booting.

---

### Post by Seb71 on 2011-11-09
Yes, you can start Windows install with an un-partitioned disk (the same is true for Ubuntu). During Windows install, you will be asked to create and format the partition. If you want multiple partitions, you can create and format the other partitions after Windows is installed.

---

### Post by Hosmion on 2011-11-09
> **Seb71 said:**
> Yes, you can start Windows install with an un-partitioned disk (the same is true for Ubuntu). During Windows install, you will be asked to create and format the partition. If you want multiple partitions, you can create and format the other partitions after Windows is installed.
Okay.  So I am literally hitting the "delete" button on the partition and using my Windows installation disk to get on Windows?

---

### Post by Seb71 on 2011-11-09
Yes, you can delete the partitions using Live CD. But you should also be able to delete the partitions during Windows install, too (remembering that first you have to delete the logical partition and only after that you can delete the extended partition).

---

### Post by Hosmion on 2011-11-09
> **Seb71 said:**
> Yes, you can delete the partitions using Live CD. But you should also be able to delete the partitions during Windows install, too (remembering that first you have to delete the logical partition and only after that you can delete the extended partition).
Okay, deleted it.  Starting up the Windows disk now. 

I'll edit this as progress moves along.

---

### Post by Seb71 on 2011-11-09
If you want to make more partitions, keep in mind the following restrictions:
- on a hard disk drive you can have maximum 4 primary partitions or maximum 3 primary partitions and one extended partition;
- because of the above rule, if you want more than 4 partitions on the same hard disk drive, one of the partitions must be an extended partition in which you create logical partitions;
- it is preferable to have only primary partitions if possible (that means if you want 1-4 partitions, make them all primary partitions);
- In Windows XP, if you create more than one partition during install, first created will be primary, the rest will be logical in an extended partition. Because of this, it is better to make the additional partitions after the Windows install is completed. In this way, you can create them as primary partitions.

---

### Post by Hosmion on 2011-11-09
I deleted the partition.  When I went to install Windows on a driver it still said that it's not in NTFS format and it wouldn't let me doing anything.  What should I do?

---

### Post by Seb71 on 2011-11-09
You first have to create the partition and only after that you can format it.

---

### Post by Hosmion on 2011-11-09
Asdfghjkl I'm so confused.  Do you have an AIM so we can discuss easier?

---

### Post by Seb71 on 2011-11-09
No. Sorry.

Which Windows version are you trying to install?

---

### Post by Hosmion on 2011-11-09
Windows 7.

---

### Post by Mark Phelps on 2011-11-09
If you install Win7 on a BLANK hard drive (NO partitions), it will automatically format for you -- creating two partitions: (1) a 100MB boot partition, and (2) an NTFS partition filling the remainder of the drive.

If an NTFS partition already exists on the drive, Win7 will offer to reformat it as part of the installation.

If the drive is formatted using Linux filesystems, the Win7 installer does not understand those and will not reformat them.

So, as mentioned earlier, you need to boot from an Ubuntu desktop CD.  Then, use Disk Utility to delete ALL the partitions on the drive.  When done, Disk Utility should show the WHOLE drive as unallocated free space.

Then, reboot using the Win7 DVD and do the install.

---

### Post by Hosmion on 2011-11-11
> **Mark Phelps said:**
> If you install Win7 on a BLANK hard drive (NO partitions), it will automatically format for you -- creating two partitions: (1) a 100MB boot partition, and (2) an NTFS partition filling the remainder of the drive.

If an NTFS partition already exists on the drive, Win7 will offer to reformat it as part of the installation.

If the drive is formatted using Linux filesystems, the Win7 installer does not understand those and will not reformat them.

So, as mentioned earlier, you need to boot from an Ubuntu desktop CD.  Then, use Disk Utility to delete ALL the partitions on the drive.  When done, Disk Utility should show the WHOLE drive as unallocated free space.

Then, reboot using the Win7 DVD and do the install.I did delete the partition.  I hit the red delete button and from the Ubuntu disk, it said the partition was "free space".  I just couldn't get anything to work.

---

### Post by Seb71 on 2011-11-11
During Win7 install, you should see now for your hard disk drive just one entry: "Disk 0 Unallocated space" (followed by the size of the disk). If you see something else, then you did not delete all the partitions.

---

### Post by Hosmion on 2011-11-15
Yay!  It worked!  Thank you so much for all of your help.  Marking thread as solved now.

---

