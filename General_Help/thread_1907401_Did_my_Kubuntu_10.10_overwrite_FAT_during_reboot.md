---
title: "Did my Kubuntu 10.10 overwrite FAT during reboot?"
date: 2012-01-11
forum: General Help
---

### Post by damix911 on 2012-01-11
[LEFT]I have a desktop system with Kubuntu 10.10 and Windows 7. Kubuntu used to be my main system, but in the last year I worked a lot with Windows (only used Linux on my laptop). Today I accidentally told Grub to start Kubuntu 10.10 (which is still the default OS). I soon restarted and switched back to Windows 7. Then I noticed that a lot of files in my FAT32 F: partition were not visible, look like they have been erased by Kubuntu. That partition is mounted in Kubuntu as /media/fat32. Could it be that Kubuntu had an old FAT table stored somewhere in RAM, which was saved to disk as part of the hibernation process, and that today was copied back on F:, effectively deleting all the files created in the last year? By running CHKDSK on F: in Windows I was able to recreate a single directory called FOUND.000 which seems to contain everything (around 13.6 GB) but file names are quite meaningless and no directory hierarchy seems to have been preserved. This directory is visible from Kubuntu but not from Windows.
[/LEFT]
 
What is the problem? How can I solve it? I would like to understand whether FOUND.000 is really my data and in that case how can I recover it. Thank you, have a nice day.

Dario

---

### Post by searchfgold6789 on 2012-01-11
It's really difficult to recover files from FOUND.000 because the files are still there, they just don't have any information attached to them like dates or file or folder names. It's all been converted to hex code or something. Try software like TestDisk - that's your only hope.

---

### Post by damix911 on 2012-01-11
@searchfgold6789 Thank you for your reply. I had tried TestDisk (from Windows 7) but it does not see any deleted file to undelete. Everything is fine to him and it shows the FOUND.000 folder as any other folder.

Why did this happened? Did I do anything wrong? Could it be considered a Kubuntu bug? Is there any signature-based data recovery software that operates on FOUND.000 folders and which will guess file types and reconstruct the files by chaining the .CHK files in a reasonable way? Under Linux, XFCE is able to visualize thumbnails of pictures, and with Gimp and Kate I was able to open some files and see that they were related to Racer and FlightGear (for Windows) that I installed a few days ago on that partition.

---

### Post by Buntumatic on 2012-01-11
I do not think Kubuntu deleted your files. Probably the partition in question wasn't umounted cleanly or you interrupted fsck when it was doing routine check, which resulted in corrupted filesystem. It could have been easily fixed from within Linux just by running fsck again. Now after Windows disk utility was involved ... Linux **file** utility still may recognize the type of those files ... do not know, not a Windows user myself.

---

### Post by oldfred on 2012-01-11
You mention hibernation. And that is likely the problem.

You cannot hibernate with two operating systems and shared data without the possibility of the problem you have. Each system has a image that it thinks the system is, then if you modify anything from another system that is in that image you have corrupted the hibernation. It does not matter whether you hibernate Windows or Linux.

---

