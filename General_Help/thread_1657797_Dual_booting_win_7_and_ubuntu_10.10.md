---
title: "Dual booting win 7 and ubuntu 10.10"
date: 2011-01-01
forum: General Help
---

### Post by riyasmp on 2011-01-01
HI guys

it would be a great help if you could help me in sorting out this dual booting issue.

My brand new laptop is HP dv6-3150SA which is shipped with 64 bit win 7. when I look at the G parted it has 4 primary partitions as follows

sda1) named after system
sda2) where win 7 is installed
sda3) recovery
sda4) HP_TOOLS

as there is 4 primary partitions i am not able to use the freed space from sda2, for ubuntu install as it keeps sayin there is already 4 primary partition. there is no option available to format this freed(unallocated space) into a logical volume as well.

I am not a technical guy but still what comes to my mind is to delete the recovery partition and then use the freed space to install ubuntu. what I want to know is

1) HP says if you make a recovery kit you wouldn&#8217;t be able to make another one and I HAVE MADE ONE ALREADY to be on the safer side.In that case deleting the sd3, Is it going to make any problems or is that sd3 ever going to be used later on for whatever reason once that recovery kit is made? Is there any chance that I wouldn&#8217;t be able to use the freed space even after deleting the recovery space? I was randomly goin through some forums and some one has opined that even after deleting the sd3 the g parted came up as 4 primary partitions ( thats what worrying me)

2) Or is it more easy to delete sd4 in this case and proceed.

I like to do it this way as it allows me to install one more distro if i need it later. please help

with regards

---

### Post by Quirion on 2011-01-01
I think you should be able to create a recovery DVD by using the HP Recovery Manager. Once you have created it and put it in a safe place, you can probably wipe out sda3 and sda4 without any risk.

---

### Post by riyasmp on 2011-01-02
Thanks for the reply

My random search results returns the HP-Tools might be used while booting. Could you tel me what could be the use of sd3 and sd4 once the recovery kit is made, and moreover a second recovery media cannot be made once the first is done.

are they (sd3,4) significant at all after the image has been burnt

with regards

---

### Post by riyasmp on 2011-01-05
eventually I got it done.

this is the way i did it

1) created recovery disk+back up+repair disk in case

2) deleted the recovery partition as its of no use once recovery disks are made

3) freed as much as space I wanted from sda2(where win 7 is

4) formatted the free space into an extended partition. made 3 logical partitions, one for ubuntu, one for the swap and the third one just if i want to install any other distro later on.

5) choose manual configuration when it comes to partitioning the disks when u install it

install was flawless. but i have got some other problems like GRUB is being deleted frequently and when you install the proprietary driver for the graphics card the screen goes blank after the boot up. i reinstalled ubuntu again and hasnt installed this driver again

---

### Post by Mark Phelps on 2011-01-06
> **riyasmp said:**
> ... install was flawless. but i have got some other problems like GRUB is being deleted frequently and when you install the proprietary driver for the graphics card the screen goes blank after the boot up. i reinstalled ubuntu again and hasnt installed this driver again

Sorry to hear you're having problems -- but please start a new separate thread for each of the problems.  Folks here tend to respond to the titles of the threads, and these All-in-one threads often get ignored.

---

