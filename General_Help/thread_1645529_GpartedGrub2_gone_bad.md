---
title: "Gparted/Grub2 gone bad"
date: 2010-12-14
forum: General Help
---

### Post by spiffydudex on 2010-12-14
I had recently set my mother up with a dual boot install of XP and Kubuntu. The reason for this move was to migrate her to a stable system that didnt need maintenance every few weeks. Everything went well and all the programs worked well.

This semester I come home from school and I find out she is low on storage space. (Pictures taking up space) 

Here is where the fun begins
After permission, I boot to a live CD use Gparted and delete the XP partition. After deletion, I extend the 2nd partition to fill the unused space. Then expand the EXT4 partition to allow for more room.
All of this completes without a problem. I reboot the machine and realize that Grub2 isn't happy and will not boot the system.

I followed these instructions for setting up Grub2 again: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

While in the process at the install portion the machine throws a fit and freezes. I turn the machine off and to my astonishment all of the partitions seemed to have been removed from the disk.

I have tried to run e2fsck and fsck but both come back with the error of a bad super block. I have also tried running the e2fsck -b with the recommended block number, but to no avail. 

Please help ASAP, my mother would be very displeased with me(haha). I am not well versed in linux drive recovery techniques.

Notes:
The drive was originally partitioned as such:
WinXP(~50gig)|Swap(1gig)|ext4(48.5gig)
After Gparted it was:
Swap(1gig)|ext4(~98gig)

---

### Post by spiffydudex on 2010-12-14
I'm out of ideas, I have spent the last hour trying to get an FSCK to work, but its nothing is working. Anyone have any ideas about what to do?

---

### Post by JC Cheloven on 2010-12-14
Phew, playing with partitions that way is always dangerous. I ran myself into problems for much less :)

Here you have a [solved] thread with a problem similar to yours. It can be a source of ideas:
[http://ubuntuforums.org/showthread.php?p=10021698](http://ubuntuforums.org/showthread.php?p=10021698)
Following that, TestDisk could be something to try.

Comprehensive advice for data recovery can be found at: 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Best of luck!

BTW: Moving your ubuntu partition to accomodate to the freed space surely took AGES, true? Much more than doing a fresh install. For future similar occasions you could consider the fresh install option. It's quicker and less prone to errors! ... Or in this case, simply deleting the files of the win2 partitiom and making of it "the photos partition" would have suffice as well.

---

### Post by spiffydudex on 2010-12-14
Thanks so much for pointing me to that page. I have since been able to  recover the partitions. Took a while to coax Grub2 to work, but in the  end everything worked out and alas I learned some more :)

Thanks for the help :razz:

Andy

---

### Post by JC Cheloven on 2010-12-15
Awesome, congrats!

If you have a minute, it is advised to mark the thread as solved when your problem is fixed (using the Thread Tools menu in red bold letters at the top of the page), and, if possible, post a little explanation so that others can benefit from your experience.

Cheers

---

