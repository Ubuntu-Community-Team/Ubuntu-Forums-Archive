---
title: "Multi booting"
date: 2009-11-30
forum: General Help
---

### Post by Dave67 on 2009-11-30
I have a plan to install window 2000, and windows XP home and Ubuntu 9.04 on two 80GB hard drives. what I would like to know is can grub handle this?  Here is the why 3 operating systems

windows 2000--for my older PC games (descent freespace) :) etc

windowsXP home SP3-Home DVR with mediaportal

Ubuntu 9.04--Using this great OS 

********************************************************

drive A will be divided 40Gb for win2000 and 40GB winxp 

drive B will be 30GB ubuntu and than 50GB for the dvr recording space for mediaportal.

how would I go about partitioning the drive spaces for both drives never done this type of install before.

Can this work or am I dreaming?

dave

---

### Post by tripolitan on 2009-11-30
Since only one operating system can run at a time, I would put all operating systems on one HD and Data on a seperate drive, 10-20GB for Windows 2000, and split the remaining between Ubuntu and XP. This utilizes the full speed of your HD channels (reducing access time).

I'm not sure if it is possible to install 2 versions of windows on one HD, I have never tried it. If this is possible, install XP first, no updates, then windows 2000, no updates. Always Install Linux LAST as it will automagically configure grub for you, dont forget to clear one 1GB partition for linux swap.

---

### Post by oldfred on 2009-12-01
You can install lots of systems but windows need to be in primary partitions of which you only have 4 primary or 3 primary and one extended. Fortunately Ubuntu can be totally in extended partitions.

Using 5 drives
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_") 

Multiple copies of windows will also combine their boot into one of the windows so you can choose which windows to boot (boot.ini). From Grub you only can then boot directly to one windows since the other is not complete. A work around is to move the boot flag (*) to the new partition for windows. You only can boot the last windows installed from windows but grub can then see both.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Dave67 on 2009-12-01
thanks for the fast reply,

I was not thinking I would be booting into another windows system within windows. I wanted to use grub to see both windows and linux partitions  I have read a document on Microsoft duel booting win2000 and winxp which suggested I install win2000 first than winxp this way the corrupted MBR would be fixed according to the Microsoft doc. But if grub sees them all than I will not worry win2000 is more for older games and the primary use of this system is for a Home DVR with Winxp. I will surf the web with ubuntu. :) I currently duel boot XP and Ubuntu 9.04. Why no updates on the window? I need the SP3 to run mediaportal


dave

---

### Post by oldfred on 2009-12-01
If you do not want or need to boot both windows from windows see this about moving the boot flag before installing the second version of windows:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by tripolitan on 2009-12-02
"No updates" was suggested for time saving, in case the installs do not work. I should have said, no updates until everything is working...Good luck

---

### Post by Dave67 on 2009-12-05
what would be the best software for partitioning the drive I do not think I can use the windows cd's partition magic  or something like that?

---

### Post by samg34 on 2009-12-05
The first option gives you more control over the partitions,
but the second option it faster
i would go the the second if i were you

you could download the live CD ISO from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
burn it to a CD
put it in and reboot (make sure the bios runs the live CD)
under administration click GParted
use this to partition your win OSs to the size you want
then click install Ubuntu on desktop
make it on its own partition
viola!!! (the bios can handle up to four partitions)

OR

go to [http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi)
and change size to your desired size
Magical!!!

---

### Post by Dave67 on 2009-12-06
From the microsoft doc I read I need to install the windows versions in this order 

win2000 25GB
winxp SP3 30GB 

than Ubuntu  24GB + 1GB swap 

:)


I if installed ubuntu first I think I will run into issues I have not done an install that way unless it was just ubuntu and I have never used the wubi program but I looked at it  intriguing to me, I will have to read more about that seems it would make the install easier plus it seems to mount the iso and install from that.

How big a swap partition does to default of Ubuntu create?

I have the ubuntu

---

### Post by oldfred on 2009-12-06
I generally do not recommend Wubi as it runs as a program inside windows, so if windows is corrupted you will not be able to boot Ubuntu. But if you are primarily a windows user and just want to see Ubuntu it will run faster and be easier to boot as Wubi than just using the liveCD. If you have space, can add two partitions you can easily set up dual boot of Ubuntu.

I would put both windows on one drive and Ubuntu on the other. Then if one drive ever fails you still can boot the other drive. Since Ubuntu/grub are more flexible about booting other systems you make the Ubuntu drive first so BIOS boots it and then you can choose Ubuntu or either windows ( if you install them as discussed above).

Ubuntu does not create a default size swap, swap should be the same as RAM if you have over 1GB RAM. Twice RAM if you have less than  1GB. I usually recommend at least 2GB swap as a minimum as most systems seem to have that or will be upgraded to that in their lifetime.

---

### Post by Dave67 on 2009-12-09
Once I decide to either just install winXp and ubuntu or all 3 of them I know one of them will work with some configuring with the settings on winXp  plus I am now thinking will I have enough time to play them all most likely not. I will post back what I decide to do. now I am deciding................ 

thanks 

dave


:-$ I am hunting Windows....

---

