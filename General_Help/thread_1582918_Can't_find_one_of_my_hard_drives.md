---
title: "Can't find one of my hard drives"
date: 2010-09-27
forum: General Help
---

### Post by ArnsteinK on 2010-09-27
Earlier I had two physical hard drives in my computer, one with Windows and one with Ubuntu. Now I have a new computer and have installed these hard drives in it. I run Windows 7, and I can find the Windows disk, but not the Ubuntu disk. This doesn't surprise me, as Ubuntu is another filesystem, however, earlier I could format it with a partition manager, but now I didn't even find it with that! Any ideas about what to do?

---

### Post by 0N3 on 2010-09-27
Im guessing you formatted the second (ubuntu) drive in Ext3 or Ext 4 Windows cant read Ext3 or Ext 4  whereas Ubuntu obviously can and it can also read many others including NTFS and FAT32 ect......

---

### Post by ArnsteinK on 2010-09-27
Yes, I know, but do you know of any Windows 7 programs that can find this disk and  format it? I have to reinstall Ubuntu on it.

---

### Post by 0N3 on 2010-09-27
you can also open up your XP Vista or Windows 7 Menu by clicking on start and right clicking on "My Computer / Computer" from there select "Manage" a new window opens in the left hand pane look for "Disk Management" click that give it a few seconds to Load Virtual Disks it should show both Disks there. From there you can format shrink and partition any of your disks but do it with caution.

---

### Post by 0N3 on 2010-09-27
Let me know if your stuck of if you sorted it.

---

### Post by ArnsteinK on 2010-09-27
I only find the NTFS-disks there :/

---

### Post by 0N3 on 2010-09-27
If your only wanting to format the partition before installation the Live CD will do this for you prior to installation go ahead with the live CD and format what you have to if the Live CD doesn't detect the disk i am guessing theres a problem with your HDD

---

### Post by 0N3 on 2010-09-27
Can you open a terminal and type:

sudo fdisk -l

Post the output here.

---

### Post by ArnsteinK on 2010-09-27
Checked the bios now, didn't even find it there. Guess it's broken then :/

---

### Post by ArnsteinK on 2010-09-27
I don't have any partition with ubuntu now, and not a live disk either by the way.

---

### Post by 0N3 on 2010-09-27
Are they IDE or Sata Disks you said you installed them.

---

### Post by ArnsteinK on 2010-09-27
Well, they worked on my old computer. 

They are SATA, both are Western Digital 1tb. Don't know the model name.

---

### Post by 0N3 on 2010-09-27
Double check your connections on the motherboard and both have a power source? Im just trying to eliminate everything i can think of
Try download another live CD and burn it and see if it detects the both HDD's?

---

### Post by ArnsteinK on 2010-09-27
Thank you for helping me! I've opened the cabinet and double checked everything, unfortunately. Will get a live cd now, but I doubt it will find it when the bios don't!

---

### Post by 0N3 on 2010-09-27
More then welcome best of luck with it let us know if Live CD does any help

---

### Post by psycho5 on 2010-09-27
Hey, I've had similar problems, also with a Western Digital 1Tb disk, sometimes BIOS doesn't see it anymore.

What I usually do is switch off the computer, and plug the disk into another sata connector, turn it on, then BIOS starts to see it. As does ubuntu and windows.

---

### Post by ArnsteinK on 2010-09-27
Tried that, didn't work, but after that I tried to switch the power cables, and it worked. Apparently I just had a dead power cable. After that I formatted it in Windows 7. Thanks for all the help! :)

---

### Post by 0N3 on 2010-09-27
:popcorn::guitar:

---

### Post by psycho5 on 2010-09-27
Mark the thread as solved :D

---

