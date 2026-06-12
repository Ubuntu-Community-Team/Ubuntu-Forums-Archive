---
title: "New system disaster... HDD problems"
date: 2012-02-07
forum: General Help
---

### Post by dkolars on 2012-02-07
Thought I'd update my hardware, as my 6 yr. old Dell was starting to cough and wheeze under the load of many websites...  So, built my own system.  Moved the HDD's over and have had nothing but problems...  After about the 4th or 5th attempt, it finally found the boot drive.  Then, could not find the 2nd internal data drive.  THEN, could not find any of the 5 external USB drives... 

My fstab file lists the drives by UUID, so have no idea why it was not finding them...

So, moved the drives back to the original system so I could "check things out"... Took about 3 hrs. to get them working in the orig. system!!  Now, I discover that somehow, in all of this mess, my external drive that contained about 100 GB of videos & pics has been re-written to become a boot drive...  a mirror image of my HD1...  NOT happy, am I...:mad:

What the Hell does one have to do to migrate to a new system?

Also, HD1 is listed in Disk Utility as /dev/sdb2... HD2 (data, internal) is listed as /dev/sda1...  Then, the drives jump to sdg thru sdk... what happened to sdc, sdd, sde, etc.?

And HD7 is now mounted as HD7_   I see this a lot... Ubuntu seems to just mout things where it wants to sometimes...

All suggestions welcomed...  I dream about "plug and play" sometimes...

---

### Post by ankspo71 on 2012-02-08
In the new computer, did you boot into bios to make sure that all of your drives are detected and configured to boot in the correct order? If the hard drives are not booting in the correct order then it will cause *ubuntu to think sda is sdb. See this "Hard Disk Boot Priority" bios settings example here:  [http://members.iinet.net/~herman546/p1.html#Changing_the_hard_Disk_Boot_Priority](http://members.iinet.net/~herman546/p1.html#Changing_the_hard_Disk_Boot_Priority) . I'm reading that not every bios will have this feature though.

A mirrored drive can happen when the same drive is mounted twice under two different device names. Double check for any mistakes in fstab. Open fstab in an editor and then open a terminal window and run these two commands:
```
sudo fdisk -l
sudo blkid
```
Then compare the three (fstab,blkid,and fdisk) to see if they all are all correct. Pay close attention to the size and positions (start and end) of the partitions in fdisk too. If we move partitions around we can can cause *ubuntu to mount partitions under unexpected device names. I've done this before, and this how-to helped me get that sorted out: [http://journalxtra.com/linuxsanity/how-to-reorder-linux-drive-partition-numbers-2768/](http://journalxtra.com/linuxsanity/how-to-reorder-linux-drive-partition-numbers-2768/)

Other than that, I'm not sure what could have happened.
Hope this helps.

Edited: Added link and fixed typo

---

### Post by dkolars on 2012-02-08
When I fired up the new one, I set boot order in BIOS for CD 1st, HDD 2nd, removeable media 3rd.  Saw no option for setting anything about my hard drives???

fstab is (was) fine... I had a LOT of problems a while back, and someone suggested using UUID #'s to eliminate the problems... that worked, and has worked ever since...  I did discover that where in internal drives are plugged into the motherboard makes a lot of difference!!

I looked at the link you suggested and could see nothing there that related to the naming convention "problem" that I have...  

I did mirror my HD1 before I did the switch, but I did that to HD6, and that caused some confusion when I started up the new system, as there were now 2 boot drives... I was able to, once I had the system running, delete the mirrored image and re-format the drive.  But why something put a mirror on HD5 is a puzzle... I'm sure that there is no way to recover what was there, and the more I think about it, the more I realize what was there...  stuff that can never be re-created!!  Bums me out, big time...  Hours of videos of live performances at conventions I've been to/played at, pics for a book I'm working one, etc.  Think that I'll get a couple of extra HDD's just to back things up on...  Grrr...

---

### Post by ankspo71 on 2012-02-08
Hi, 
Try using testdisk to recover the files. It is available in the repositories, and here instructions on how to recover from a reformatted partition: [http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformatted_partition](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformatted_partition)


It could have very well been the 2 boot drives that confused *ubuntu like you said. It is probably better to work with one hard drive at a time on the new computer to get it up and running, starting with the main drive of course. Then connect each other drive one at a time, and configure them in fstab one at a time. I think that way it would be easier to find any more clues.

Hope this helps.

---

