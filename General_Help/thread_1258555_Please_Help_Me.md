---
title: "Please Help Me"
date: 2009-09-05
forum: General Help
---

### Post by Sf3d0 on 2009-09-05
Recently I installed Ubuntu on my computer..but the problem is that I installed it on a hard disc that was in use from my windows..that was a second disc, with my data..It was years of my work saved over there and now I cannot use it with windows..I'm afraid my data is lost and I'm really terrified..

---

### Post by Liolikas on 2009-09-05
I hope you not chosen "use entire disk".
Just show what you have in hdd with:
sudo fdisk -l

---

### Post by Sf3d0 on 2009-09-05
> **Liolikas said:**
> I hope you not chosen "use entire disk".
Just show what you have in hdd with:
sudo fdisk -l
i've chosen it

---

### Post by Liolikas on 2009-09-05
That is not good just for sure try:
sudo fdisk -l
in terminal.

---

### Post by Sf3d0 on 2009-09-05
then any way to boot ubuntu and use them this way..? to copy them to an other disk..?

---

### Post by Liolikas on 2009-09-05
Use windos program simillar to fdisk maybe Partition magic?
In it you can see partitions/hdd/free space and understand what you really have. But if you chosen use entire disk so basically you can start searching for data restoration after format software.

---

### Post by Sf3d0 on 2009-09-05
restore 500GBs..?? that's gonna take years..

---

### Post by Efwis on 2009-09-05
Windows won't show a hard disk that is formatted for linux.

when you installed ubuntu it formatted the disk to install it as linux won't install on a ntsf partition. I hate to say this, but there is a 99.9% probability that you lost all that data unless you made a backup before installing ubuntu.

---

### Post by Liolikas on 2009-09-05
>Windows won't show a hard disk that is formatted for linux.
true, but non microsoft software like partition magic can do this 

(rip partition magic after vista release, you standed on M$ way well long time) :(

---

### Post by Sf3d0 on 2009-09-05
[http://img509.imageshack.us/img509/3383/disks.jpg](http://img509.imageshack.us/img509/3383/disks.jpg)

---

### Post by Liolikas on 2009-09-05
> **Sf3d0 said:**
> [http://img509.imageshack.us/img509/3383/disks.jpg](http://img509.imageshack.us/img509/3383/disks.jpg)
Because widos fails to see what format is in disk1 so I can guess it is not ntfs. So you formatted entire disk1. Sorry.

---

### Post by Efwis on 2009-09-05
as you can see in that image, it shows a blank hard disk, however it is actually your linux install.

---

### Post by Sf3d0 on 2009-09-05
then any way to boot ubuntu and use the files this way..?

---

### Post by Efwis on 2009-09-05
upon restart of the computer you should have a menu show up with ubuntu as the default OS. did you follow through with the complete install? or did you stop halfway through it?

---

### Post by twright on 2009-09-05
Right, it looks like you have probably told it to delete all of your data but with a bit of luck you might be able to get it back:

[LIST=1]
[*]Firstly, until you get whatever data back [COLOR=Red]**stop using that computer/drive **[COLOR=Black]- everything you do with it makes it less likely your data can be restored.[/COLOR][/COLOR]
[*][COLOR=Red][COLOR=Black]Secondly boot into a Ubuntu livecd, go online and have a good long read of this tutorial: [http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)[/COLOR][/COLOR]
[*][COLOR=Red][COLOR=Black]Carefully go through the steps and you should be able to recover as much data as possible.[/COLOR][/COLOR]
[*][COLOR=Red][COLOR=Black]Needless to say, in the future you should always keep a backup - whether it be hard drive failure or human error there are many ways you could loose your data otherwise (I should think it has happened to/will happen to all of us sometime).[/COLOR][/COLOR]
[/LIST]
Good luck

edit:
This is presuming you have lost all of your data (others have posted whilst I was typing). If not then good for you.

In that case you could just copy the data off using the livecd.

---

