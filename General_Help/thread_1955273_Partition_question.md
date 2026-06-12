---
title: "Partition question"
date: 2012-04-09
forum: General Help
---

### Post by xlearner on 2012-04-09
Hello All,

I have a question that is related to GRUB but is not completely apt for this discussion. I am asking anyway. 

My issue is opposite of the question asked in this thread, I want to add more entries to my GRUB menu. I have partitioned my hard drive. The output of my df: 
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            418137888   8216812 388680912   3% /
udev                   3041404        12   3041392   1% /dev
tmpfs                  1220516       924   1219592   1% /run
none                      5120         0      5120   0% /run/lock
none                   3051288      3468   3047820   1% /run/shm
/dev/sda7	      28967928	21603656   5892784  79% /home

(Actually the view here is messed up as the tabs are not properly aligned. I have attached this file in text format. If viewed in gedit, the tab & spaces will be properly aligned.)

As you can see there are two partition: /dev/sda5 and /dev/sda7. The partition /dev/sda5 is around 435 GB and is mostly unused whereas /dev/sda7 is only 30GB. But this is my current working partition and is 75% used. So I want to change my working partition from /dev/sda7 to /dev/sda5.

But for some reason /dev/sda5 does not appear in the grub boot menu. What should I do to add this partition in the boot menu. 

When I searched, I only found ways for removing from GRUB. But nothing much on adding entries to GRUB. Can someone advise me as to how this can be done? 

Thanks
Xlearner

---

### Post by oldfred on 2012-04-09
I moved you to a new thread as yours is not related to grub at all.

You are using both partitions. The default standard install is just / (root) and swap. We often suggest the separate /home to make it easier to reinstall. But /home is automatically used in / and not separately booted. It just has your user settings in hidden files and your data.

Normally I suggest 10 to 25GB for / (root) when you have separate /home or separate data partitions as the system does not require lots of room. It seems like you have reversed the size of your / & /home partitions. Depending on where they are on the drive you may be able to move/resize with gparted from a liveCD. 

You can add gparted to your install but cannot use to to resize while using the system. But a screenshot from gparted shows the partitions locations in a graphical way which for most is the easiest way to understand it. Download gparted and post a screenshot of you partition layout. If you need help on that post back and give version you are using. 

You can also post this from terminal to see partition layout, use code tags (highlight like copy & hit # in edit panel above your message):

sudo fdisk -lu

---

### Post by grahammechanical on 2012-04-09
The Grub menu only shows operating systems and the partitions that they are on. If you had an operating system on sda5 the Grub could be made to detect this by a simple command.

If you some how put a option to boot into sda5 without there being an operating system on it, then the boot process would fail.

What you can do is resize those partitions. Run the live CD and at the Live Desktop open the Gparted Partition Manager. You can shrink sda5 and make space to grow sda7.

I may be wrong but from that read out it seems to be that Ubuntu is installed to sda5 for this symbol ( / ) at the end of the second line tells me that is where Ubuntu is. 

Also sda7 seems to be a separate /home partition. So, I   do not understand when you say that sda5 is not showing in the Grub menu.

But nonetheless, you can still resize the two partitions so that the sizes are reversed. 

sda5 = 20 - 25GB and sda7 = all the rest.

Please see this

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by xlearner on 2012-04-10
Dear Oldfred & Grahammechanical,

Thanks a lot for replying back. Also thanks Oldfred for creating a new thread. 

So as you have suggested, I have attached the screenshot of gparted. As one can see I have three partitions:
/dev/sda5 of size 405.12GB; /dev/sda6 of size 22.35GB; /dev/sda7 of size 28.07GB. /dev/sda5 & /dev/sda7 are ext4 whereas /dev/sda6 is unpartitioned. 

When I created these partitions and installed ubuntu 11.10, my original intention was to have two paritions. One partition of large size (like 400 GB) which will have a stable OS version running. The other partition will be of smaller size (55 GB) and will have an experimental version of the OS running. 
But recently I realized that I did not do things correctly. Now I have three partitions: /dev/sda5, /dev/sda6 and /dev/sda7. The partition /dev/sda5 does not even appear in grub menu. The parition /dev/sda7 is the only one that shows up in GRUB menu and has become my main partition.  

So at this point, I would like to do two things:

- Make /dev/sda5 come in the GRUB menu. It seems that this partition does not have ubuntu installed on it. That is why it does not appear on the GRUB menu. (But my belief is that I had originally installed ubuntu on this partition). Is there anyway to check if this parition has ubuntu installed on it or not? 

- Merge the paritions /dev/sda6 and /dev/sda7. 

So can you suggest how I can accomplish both these steps?

Thanks again!

Xlearner

---

### Post by oldfred on 2012-04-10
Gparted is showing some sort of error on sda6. If you click on the error flag what type of error is it. If you are sure you have no data in it you can just delete it, if it will let you before correcting the problem.

But your / (root) is very large and /home not so large. You can easily shrink /, but expanding /home left will be a slower process as it has to move all data. Be sure to have good backups when doing anything in gparted. Any power failure or interruption can totally corrupt system. Just let it finish normally.

You still have room for another 20 or 25GB / partition after shrinking / if you want. If you do more than one change do each separately. Or first delete sda6 and click on the checkmark to run it. Then shrink sda5 and run that change. Then create a new sda6 (may be sda8?) 20GB for another system and run that. Finally move sda7 left into the remaining free space.

---

