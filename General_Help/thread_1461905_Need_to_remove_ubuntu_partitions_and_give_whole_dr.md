---
title: "Need to remove ubuntu partitions and give whole drive to back to Windows"
date: 2010-04-24
forum: General Help
---

### Post by DougieFresh4U on 2010-04-24
Currently using live-cd to post.
This machine has 160GB hard drive. Windows XP was on machine to begin with. I installed Ubuntu Karmic to a partition then I made another partition for Ubuntu Lucid. 
I need to remove both Ubuntu partitions and let Windows XP have the whole hard drive back (I am giving this to my sister and use the machine I built)
How can I safely remove all Ubuntu? Using live-cd, could I just go to gparted and delete both partitions and it will boot to Windows with out any drama?
Thanks for any help

---

### Post by Yogotiss on 2010-04-24
if you have a retail copy of XP you can use that to blow away any patition to make it one. then just install XP

---

### Post by Kljuka on 2010-04-24
It would be safer to delete partitions within Windows.

---

### Post by DougieFresh4U on 2010-04-24
> **Kljuka said:**
> It would be safer to delete partitions within Windows.

OK, how would I go about doing this?
Thanks
I do not have a Windows cd to reinstall WinXP

---

### Post by Kljuka on 2010-04-25
You need a program to manage partitions.
You can buy Partition Magic (or some other) or go with free alternative (google says EASEUS Partition Master or Partition Wizzard etc)

---

### Post by DougieFresh4U on 2010-04-25
**Please keep in mind I am not leaving Ubuntu, just switching machines**
So I have managed to get rid of the Ubuntu partitions. And I am able to boot into Winxp.
I now have WinXP on 50GB and have 100GB of 'free' space. Now I need to 'reclaim' that 100GB back to WinXP.
So I right click on 'My Computer' from the start menu and select 'Management' and then select 'Disk Management'. This where I get lost as I am not sure how to resize as it ask about making it 'primary' or 'extension' and then I need to make the size.
Please, any help would be great.
Thanks

---

### Post by kelvin spratt on 2010-04-25
Download parted magic delete the partitions you don't need and resize your windows partition. Or delete both partitions format to ntfs boot up xp right click menu right click on my documents and move documents and settings to your new partition that should be D.

---

### Post by Gatemaze on 2010-04-25
You can have up to 4 primary partitions and as many as you want extended under a primary one... In brief if you are trying to do

C: 50 GB
D: 100 GB

and have only two partitiions then go ahead with primary... in any case if there are other "hidden" primary partitions it shouldn't let you create a fifth one.

---

### Post by abanderas on 2010-04-25
not necesarry to 'reclaim' 100 Gb free space back 2 winXP - leave separately in a partition for (ex. work) - is more better do not disturb windows instalation partition with any partitioning or  defragmentation tools.

---

### Post by Gatemaze on 2010-04-25
> **kelvin spratt said:**
> Or delete both partitions format to ntfs boot up xp right click menu right click on my documents and move documents and settings to your new partition that should be D.

IGNORE HIS POST AND DO NOT DELETE BOTH PARTITIONS... as from what you said XP are on one of them.

Dude, deleting both partitions will destroy his operating system... <snip>

---

### Post by DougieFresh4U on 2010-04-25
Gonna mark this solved and would prefer **'thread closed'**
I reformatted the 100GB free space and using it as 'extra' . I believe I am all set.
Thanks to all who supported me on this, even though it was a Windows problem

---

