---
title: "Error: no such partition. Plus no USB.."
date: 2012-06-02
forum: General Help
---

### Post by rommieuserxero on 2012-06-02
Hi, I have a stupid problem..

I had windows 7 installed then I added Ubuntu just fine but when I was in Windows and in the partition manage menu, besides the primary partitions there was a group of "extended" partitions. First was "free space" then a blank one which was my Ubuntu partition and then a partition I made in windows awhile ago. I then went to create a new partition in said "free space" and it tried to make a partition using that free space and the Ubuntu partition because it didn't know what was what...... :mad:

Now then after the error I restart my computer and find myself looking at:
"Error: no such partition."
"grub rescue "
Then after my face became red I put in my Ubuntu (10.04) cd, restarted and pressed F12 to get to boot options,The only problem was my only optical drive is a external usb cd drive :frown: and there was absolutely no power to usb ports.


Now even if usb worked hence optical drive, I am not sure what to do.

please help!
Thank you vary, vary much.

---

### Post by Mark Phelps on 2012-06-03
If you already had the maximum of three primary and one extended partition, when you created another from inside Win7, you most likely converted your partitions to Dynamic Disks -- which Ubuntu can't see or use.  That would explain the inability for it to boot now.

To check this, boot into Win7 and look at the partitions (MS calls them "drives") in the Disk Management tool and tell us what is there.

---

### Post by rommieuserxero on 2012-06-03
> **Mark Phelps said:**
>  
To check this, boot into Win7 and look at the partitions (MS calls them "drives") in the Disk Management tool and tell us what is there.

Well, I'm a noob. I don't know how to boot into windows 7 nor how you say to check..

(Note: As said above I can't use cd drive, if it is required.)

---

### Post by rommieuserxero on 2012-06-03
Well the problem was kinda solved.
I went out and got a internal optical disk drive and installed it, put my Ubuntu CD in and booted off of it. This obviously could not be done with a external optical drive.

Then checked the partitions and there was no swap, no / partition, no /home partition, just Windows' partitions and a ntfs partition I made in windows. Basiclly all Ubuntu made partitions were nuked....

But I backed up my goodies literally 20 minutes before this all happened. Anyways I made my /boot, my linux swap, my / and my /home and installed and I'm typing this from Ubuntu now.

So all is well. Now. Not sure why Win7 nuked my ext4 partitions, oh well, fixed.


Just wondering though, my ntfs partition I made in windows can be mounted and unmounted in the folder system in Ubuntu but just now when installing Ubuntu I tried making a fat32 partition because both Windows and Ubuntu know it but it required me to mount it... but my ntfs partition I made in Windows isn't permanently mounted.. Maybe I am noobbing it up in here but can I not just make a non permanently mounted data partition with the Ubuntu cd?

Anyways, thanks,
Rommie.

---

