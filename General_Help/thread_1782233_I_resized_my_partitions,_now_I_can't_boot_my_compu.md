---
title: "I resized my partitions, now I can't boot my computer"
date: 2011-06-14
forum: General Help
---

### Post by notgary on 2011-06-14
**The Background**
I have three partitions on my computer - one for Ubuntu, one for Windows 7's boot folder, and a third for the rest of Windows 7, in that order. The two Windows partitions were created automatically by the Windows installer, not manually by me.

Earlier today, I booted up a Live CD so I could adjust the size of the two main OS partitions so I could move unused space from Windows, where it wasn't being used, and reallocated it to Ubuntu, where it was needed. This is how I went about it:

[LIST=1]
[*]I shrunk the main Windows 7 partition  and then moved it to the right to fill in the newly freed space.
[*]I moved the Windows 7 boot partition to the right, into the space left by the Windows 7 main partition, with the size remaining unchanged.
[*]I extended my Ubuntu partition to the right to fill the space left by the two Windows partitions. I also extended the Ubuntu partition to the left to fill a few megabytes of space that, for some reason, had been left unallocated by the installed.
[/LIST]

I did this all using GParted, and no error messages were returned.

**Now the problem**
When I rebooted my computer, I was able to see the manufacturers splash screen (the one with the F2, F12 options on it), followed by the prompt for my hard drive password, which was expected. When I entered the password, the computer immediately rebooted and the splash screen and password prompt were presented again. This cycle continues indefinitely until I press the power button to turn off the computer.

Based on what I've said in the background, can anyone figure out what's gone wrong, and how to fix it?

---

### Post by Quackers on 2011-06-14
Windows 7 does not enjoy having its partitions manipulated by other software. Windows Disk Management should be used where possible. The C: drive should also be defragmented first.
You may need to repair the file system or the bootloader.
Running a chkdsk from the Windows repair/installation disc may be a good place to start.

---

### Post by notgary on 2011-06-14
Unfortunately I don't have access to the Windows installation disk. It was a digital copy distributed by my school, and each student is only allowed a single copy.

Is there any way I can fix this on the Ubuntu side? I know I can reinstall Ubuntu and just tell it not to format the existing Ubuntu partition and that'll fix it, but I'd prefer to try a less brutish solution first.

---

### Post by misterbreadcrum on 2011-06-14
I had this problem when trying to resize my partitions with Gparted on a live CD.  What I ended up doing was unchecking the boot option on the main drive where windows and ubuntu were installed.  I finally figured out I had to go back, boot from the live cd, open Gparted from there, and recheck the drive as Boot.  Hope this helps

---

### Post by Quackers on 2011-06-14
While you had the system running you should have created a repair disc with option 1 in the link below.
You should still be able to download one from option 2.
[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

---

