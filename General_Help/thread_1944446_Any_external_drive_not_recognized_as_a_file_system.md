---
title: "Any external drive not recognized as a file system"
date: 2012-03-21
forum: General Help
---

### Post by aronstandley on 2012-03-21
I've tried a variety of thumb drives and external hard drives in my Asus EEE (1005HA, running the latest Ubuntu distro), and they all have the same pattern -

They flash up as an accessible folder in the file system window navigation, then disappear. They're showing up in the file system under /media, but when I try to open them, an error message shows up, saying that the file isn't recognizeable as a file system.

How can I move forward?

---

### Post by Mark Phelps on 2012-03-21
There's nothing inherent in Ubuntu that would prevent it from reading or writing thumb drives or external drives.

Unfortunately, those tend to come pre-formatted, and in those cases, they are formatted using MS Windows filesystems.

If you simply remove or unplug one of those from an MS Windows PC, the filesystem can be marked as "dirty" and, to prevent filesystem damage, Linux will only mount them read-only after that.

If you can, try connecting them to an MS Windows PC, and then "safely remove" each of them.

If that doesn't work, you may have to run Check Disk against each of them on an MS Windows PC.

---

### Post by Dragonbite on 2012-03-21
It may need to be reformatted. I've had issues with switching between Windows and Linux even though the USB is Fat32.

Having Windows format it as Fat32 is better than Linux formatting it as Fat32. From my experience Linux does a better job of detecting partitions/drives formatted by Windows, than Windows finding partitions/drives formatted by Linux even if it is a format Windows should know (Fat32, NTFS).

In Linux you could install GParted and run that.  You select the physical disk from the dropdown list in the upper right corner.  Then at least you can see what Linux sees it as and may help in finding out why it won't keep it opened.

In Windows you can right-click on Computer and go to Manage and then Disks.  

I have a digital camera also that does this and it is really annoying.

---

### Post by JodiBosa on 2012-03-22
run dmesg and look for messages regarding your drive.  It'll typically be /dev/sdc or /dev/sdd.  Then you can mount the filesystem using:

> mount /dev/sdc1 /mnt

---

