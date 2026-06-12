---
title: "Problems installing"
date: 2011-10-24
forum: General Help
---

### Post by hokano on 2011-10-24
hello ubuntu forums!
I am terribly sorry if this is in the wrong section as I never really use forums. 
Basically, when I try to install ubuntu on my HP dv6, it has no "install alongside" option.
if I use the "something else" option, it made my Windows 7 installation bluescrean. 
I'm at the end of my tether here as I love ubuntu, But I've tried everything...
I've created partitions in windows, and both formatted and left unformatted to see if that works, but no matter what I do, gparted doesn't recognise my partitions propperly. 
I know it's a dynamic disk, but I'm not sure if that would cause any problems at all.
Wubi fails at installation too. :(
I'm trying to use ubuntu 11.04 for installation. 
Please help. thankyou very much! :D

---

### Post by bcbc on 2011-10-24
Yes, dynamic disks are not supported by linux.

---

### Post by oldtimer7777 on 2011-10-24
You need to install it the old fashioned way..

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **hokano said:**
> hello ubuntu forums!
I am terribly sorry if this is in the wrong section as I never really use forums. 
Basically, when I try to install ubuntu on my HP dv6, it has no "install alongside" option.
if I use the "something else" option, it made my Windows 7 installation bluescrean. 
I'm at the end of my tether here as I love ubuntu, But I've tried everything...
I've created partitions in windows, and both formatted and left unformatted to see if that works, but no matter what I do, gparted doesn't recognise my partitions propperly. 
I know it's a dynamic disk, but I'm not sure if that would cause any problems at all.
Wubi fails at installation too. :(
I'm trying to use ubuntu 11.04 for installation. 
Please help. thankyou very much! :D

---

### Post by hokano on 2011-10-25
hi there, thank you all for your responces, I'm afraid I'm not sure which part of the website you where trying to show me
Plus, just for simple use, is there any way I can convert my main hard-drive to a basic drive without wiping windows 7? if not, can I convert any of the partitions to basic and leave the rest as dynamic?
Thank you all very much for your help, it is very much appreciated :D

---

### Post by bcbc on 2011-10-25
Microsoft is able to switch to dynamic on the fly, but state that you should backup data, delete all partitions, and recreate from scratch to switch from dynamic.

There are some tools that seem to be able to switch from dynamic, but I believe you'd first have to remove any dynamic partition not contained in the MBR partition table. Either way you should expect to backup everything and be prepared for failure.

There is no way to share dynamic/non dynamic on a single physical disk (at least that I am aware of). You could probably add a new drive, but in that case, you shouldn't mount your windows one from linux.

If you are just trying out Ubuntu then I suggest either virtual box or vmware - this will give you a good idea. Or try it in 'live mode' from a bootable USB or CD.

---

### Post by oldtimer7777 on 2011-10-25
It would be faster and easier if you just wipe the entire hard drive and do an Ubuntu installation. You can install Windows in Virtualbox for the few things you still need to do with it, until you can get a handle on how to use Linux natively to do the same things you did with Windows. Just a suggestion if you want less of a headache.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **hokano said:**
> hi there, thank you all for your responces, I'm afraid I'm not sure which part of the website you where trying to show me
Plus, just for simple use, is there any way I can convert my main hard-drive to a basic drive without wiping windows 7? if not, can I convert any of the partitions to basic and leave the rest as dynamic?
Thank you all very much for your help, it is very much appreciated :D

---

### Post by hokano on 2011-10-26
Normally I would just wipe the disk and re-install everything, But I bought a laptop with windows 7 pre-loaded, I can use Ubuntu by it self because I used to use it all the time. But I do like to have windows 7 on the side as a "just in case" sorta thing. The only thing I have is the Hp restore disks I had to make. could I change the hard drive by using them?
I have an Idea, just not sure if it's a legitamet idea, I was thinking download the .iso of windows 7, and then use my code from the bottom of my laptop to re-install, would this be alright? or is that illegal?
I miss ubuntu quite a lot right now haha :/ so much simpler once you get the thing going...
I'm just not really prepared to wipe my disk as I would lose my instalation of win7. and it's a laptop, so it only has one harddrive
Stil thankyou all for your help, and I realy hope there is a way I can sort this thing out

---

### Post by bcbc on 2011-10-26
Your HP restore disks should be able to repartition and restore the computer to factory state. Even if you had a windows 7 DVD you'd have a lot of work getting all the software drivers installed - without an HP driver utility disk. So a restore would likely be easier than a fresh install.

Or just use a virtual machine. On a new computer with plenty of ram (4+GB) it works fine.

My feeling on dynamic disks - most people use them to get around the 4 max primary partitions. If you remove the 'dynamic' ones - the ones that aren't in the partition table, and merge back that free space, then there's really no difference other than the fact that they're partition-type sfs instead of ntfs. So a partitioning tool that claims to be able to switch them from dynamic to normal will probably be able to do it easily (without losing data or rebuilding everything). If you've got some complex multi-disk striping setup, then obviously that's not going to work.

---

### Post by hokano on 2011-10-27
Awesome, I shall have to have a look into that, if not, I have a some one who can sort it out for me at a price, but it will be worth it to get back onto ubuntu :)

---

### Post by bcbc on 2011-10-27
> **hokano said:**
> Awesome, I shall have to have a look into that, if not, I have a some one who can sort it out for me at a price, but it will be worth it to get back onto ubuntu :)

Good luck.

PS check out this thread - oldfred does a good job collating info together and has summarised the options well: [http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

---

### Post by hokano on 2011-10-31
Thank you so much for that link! I've managed to convert my disk to basic and saved myself £30! Thank you so much!! ubuntu shall be installed tomorrow and I'll be back on the Ubuntu scene! I actually can't say thank you enough! :D 
I used EASEUS Partition Master from the previous link, I shall try to mark this as solved now :) Thanks so much people

---

### Post by bcbc on 2011-11-02
> **hokano said:**
> Thank you so much for that link! I've managed to convert my disk to basic and saved myself £30! Thank you so much!! ubuntu shall be installed tomorrow and I'll be back on the Ubuntu scene! I actually can't say thank you enough! :D 
I used EASEUS Partition Master from the previous link, I shall try to mark this as solved now :) Thanks so much people

Great! And thanks for the feedback on what you used. That will help others and we can pass along that info as well.

---

