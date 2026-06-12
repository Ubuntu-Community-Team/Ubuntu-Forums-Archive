---
title: "No free space on disk '/'"
date: 2009-07-19
forum: General Help
---

### Post by felinoel on 2009-07-19
After dual booting XP and Ubuntu, it now says there is no free space on disk '/'
Why is it saying this? Where is disk '/' how do I move the free space found everywhere else to it?

---

### Post by TeoBigusGeekus on 2009-07-19
/ is the mount point of root, i.e. your filesystem, i.e. you entire linux installation.
How much space did you give Ubuntu during installation?
Anyway, boot with a live cd, open terminal, type 
```
gksudo gparted
```
to start gnome partition manager and do any changes you like.

---

### Post by felinoel on 2009-07-19
In "Places" and below "Computer" there is a "300 GB Media" that I have never seen before, might this be what's wrong?

---

### Post by felinoel on 2009-07-19
> **TeoBigusGeekus said:**
> / is the mount point of root, i.e. your filesystem, i.e. you entire linux installation.
How much space did you give Ubuntu during installation?
Anyway, boot with a live cd, open terminal, type 
```
gksudo gparted
```
to start gnome partition manager and do any changes you like.

I thought I gave it 300 gigs, see the above post...

---

### Post by TeoBigusGeekus on 2009-07-19
No it's not wrong, it's just an unmounted partition.

---

### Post by ramnarayan on 2009-07-19
> **felinoel said:**
> After dual booting XP and Ubuntu, it now says there is no free space on disk '/'
Why is it saying this? Where is disk '/' how do I move the free space found everywhere else to it?

Hi

Now sure how you partitioned your disk while installting

In Ubuntu
open a terminal
Applications -> Accessories ->terminal and
enter the following command
```
df -Th
```

this will show you how your HD has been used, 

Or you can go to System ->Administration -> Partition Manager (this is normally not installed by default)

and use this to check how your HD is used up.

**
From what i can guess is that your partition may not have alloted too much space to you /
this / is your Ubuntu root - the place where your Ubuntu OS resides.

A good install would partition the disk in such a way that your / is kept separate from your data usually /home

So your df -hT will let us know and then we can figure what to do

---

### Post by TeoBigusGeekus on 2009-07-19
Ok, I think you might have messed something during installation.
Post us the output of the 2 following commands
```
sudo fdisk -l
```
and
```
sudo df -h
```

---

### Post by felinoel on 2009-07-19
> **ramnarayan said:**
> Hi

Now sure how you partitioned your disk while installting

In Ubuntu
open a terminal
Applications -> Accessories ->terminal and
enter the following command
```
df -Th
```

this will show you how your HD has been used, 

Or you can go to System ->Administration -> Partition Manager (this is normally not installed by default)

and use this to check how your HD is used up.

**
From what i can guess is that your partition may not have alloted too much space to you /
this / is your Ubuntu root - the place where your Ubuntu OS resides.

A good install would partition the disk in such a way that your / is kept separate from your data usually /home

So your df -hT will let us know and then we can figure what to do

```
desktop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3    2.3G  2.3G     0 100% /
tmpfs        tmpfs    975M     0  975M   0% /lib/init/rw
varrun       tmpfs    975M  104K  975M   1% /var/run
varlock      tmpfs    975M     0  975M   0% /var/lock
udev         tmpfs    975M  184K  975M   1% /dev
tmpfs        tmpfs    975M   84K  975M   1% /dev/shm
lrm          tmpfs    975M  2.4M  973M   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs    1.0M   16K 1008K   2% /tmp
/dev/sr0   iso9660    699M  699M     0 100% /media/cdrom0

```

---

### Post by felinoel on 2009-07-19
> **TeoBigusGeekus said:**
> Ok, I think you might have messed something during installation.
Post us the output of the 2 following commands
```
sudo fdisk -l
```
and
```
sudo df -h
```
```
desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2774    22282123+   7  HPFS/NTFS
/dev/sda2            2775       38587   287667922+  83  Linux
/dev/sda3           38588       38913     2618595    5  Extended
/dev/sda5           38588       38891     2441848+  83  Linux
/dev/sda6           38892       38913      176683+  82  Linux swap / Solaris

```

```
desktop:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 975M     0  975M   0% /lib/init/rw
varrun                975M  104K  975M   1% /var/run
varlock               975M     0  975M   0% /var/lock
udev                  975M  184K  975M   1% /dev
tmpfs                 975M   84K  975M   1% /dev/shm
lrm                   975M  2.4M  973M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sr0              699M  699M     0 100% /media/cdrom0

```

---

### Post by felinoel on 2009-07-19
Wow, you guys are responding fast today... I am writing down day and time for future use, usually when I come here it takes awhile before someone responds

---

### Post by felinoel on 2009-07-19
> **TeoBigusGeekus said:**
> No it's not wrong, it's just an unmounted partition.k... how do I mount it?

If this is an unmounted partition then the 20 gigs above it is unmounted too and that means my Windows has no space too... x_x

---

### Post by TeoBigusGeekus on 2009-07-19
You have installed Ubuntu on a 2.3Gb partition.
It won't be able to work on such small space. Reinstall, but this time pay attention on the partition editor during installation.
In order to assign the 300gb to Ubuntu you have to choose / as mount point for this partition.

---

### Post by drs305 on 2009-07-19
Your / partition is only 2.3GB, which is too small to support an Ubuntu installation. The partition should be a *minimum* of 5GB and 10GB or more would be my personal minimums if you plan on having your data stored elsewhere.

In any case, you are going to have to repartition your drive and take some space from another partition to grow /, or you will have to reinstall and try the install partitioning again.

From the LiveCD, if you will open gparted (System Tools, Partition Editor) and take a snapshot of what gparted displays we can provide some suggestions. To take a snapshot, Accessories, Take Snapshot. Then in the post near the bottom there is a "Manage Attachments" button. Click on that to upload the snapshot.

---

### Post by felinoel on 2009-07-19
> **drs305 said:**
> Your / partition is only 2.3GB, which is too small to support an Ubuntu installation. The partition should be a *minimum* of 5GB and 10GB or more would be my personal minimums if you plan on having your data stored elsewhere.

In any case, you are going to have to repartition your drive and take some space from another partition to grow /, or you will have to reinstall and try the install partitioning again.

From the LiveCD, if you will open gparted (System Tools, Partition Editor) and take a snapshot of what gparted displays we can provide some suggestions. To take a snapshot, Accessories, Take Snapshot. Then in the post near the bottom there is a "Manage Attachments" button. Click on that to upload the snapshot.> **TeoBigusGeekus said:**
> You have installed Ubuntu on a 2.3Gb partition.
It won't be able to work on such small space. Reinstall, but this time pay attention on the partition editor during installation.
In order to assign the 300gb to Ubuntu you have to choose / as mount point for this partition.Sigh, could have sworn I told it to install in a specified partition...

---

### Post by raymondh on 2009-07-19
how many linux installs do you have and where is ubuntu installed (which sda)?

EDIT : saw df-h and ubuntu is on sda5.  What is on sda2?  I ask because you could enlarge the EXTENDED partition to take up sda2 ... if you did not care about sda2.

---

### Post by felinoel on 2009-07-19
> **drs305 said:**
> Your / partition is only 2.3GB, which is too small to support an Ubuntu installation. The partition should be a *minimum* of 5GB and 10GB or more would be my personal minimums if you plan on having your data stored elsewhere.

In any case, you are going to have to repartition your drive and take some space from another partition to grow /, or you will have to reinstall and try the install partitioning again.

From the LiveCD, if you will open gparted (System Tools, Partition Editor) and take a snapshot of what gparted displays we can provide some suggestions. To take a snapshot, Accessories, Take Snapshot. Then in the post near the bottom there is a "Manage Attachments" button. Click on that to upload the snapshot.

[http://img515.imageshack.us/img515/5057/screenshotgrr.png](http://img515.imageshack.us/img515/5057/screenshotgrr.png)

xD, its automatic URL given to me based off of the original file name, screenshot, is screenshot grr

---

### Post by felinoel on 2009-07-19
> **raymondhenson said:**
> how many linux installs do you have and where is ubuntu installed (which sda)?

EDIT : saw df-h and ubuntu is on sda5.  What is on sda2?  I ask because you could enlarge the EXTENDED partition to take up sda2 ... if you did not care about sda2.

Only one, and Windows XP

---

### Post by drs305 on 2009-07-19
Based on the snapshot, here is one way to fix the problem, although a reinstall may be just as fast. Did ubuntu even start? It's possible it didn't even install all of the system files. If that is the case you should reinstall, although you can make the partitions first to prevent the same thing from happening again.

From the LiveCD:
1. Shrink or delete sda2 (before deleting, make sure you have no data in it).
2. Expand sda3 (extended partition). You have to select it from the bottom part of gparted, then "Resize" and drag it all the way to the left until it touches Windows (sda1).
3. Expand sda5 (linux). Select it, then Partition, Resize and drag it all the way to the left. Your linux / partition will now be approximately 276GB.
4. Once you have done all that, you can split off some of the linux partition's right side if you want to create a data partition or some other partition(s).

---

### Post by felinoel on 2009-07-19
> **drs305 said:**
> Based on the snapshot, here is one way to fix the problem, although a reinstall may be just as fast.

From the LiveCD:
1. Shrink or delete sda2 (before deleting, make sure you have no data in it).
2. Expand sda3 (extended partition). You have to select it from the bottom part of gparted, then "Resize" and drag it all the way to the left until it touches Windows (sda1).
3. Expand sda5 (linux). Select it, then Partition, Resize and drag it all the way to the left. Your linux / partition will now be approximately 276GB.
4. Once you have done all that, you can split off some of the linux partition's right side if you want to create a data partition or some other partition(s).It won't let me expand sda3?

---

### Post by drs305 on 2009-07-19
> **felinoel said:**
> It won't let me expand sda3?

Do it from the LiveCD, make sure the linux and swap partitions are not mounted (sda5 and sda6). Do this by selecting the  partitions and then Partition, Unmount or Swapoff if you see that option. 

Are you able to select sda3? You can't click on it, you have to select its line from the botton section.

---

### Post by raymondh on 2009-07-19
Do you remember how you installed? Did you, by chance, install twice?  Or if not, did you set sda2 as something/anything?

1.  Using the liveCD and access gparted from live session (aka, "try without changing...")
2.  To be sure, double check that the internal is unmounted. Another method is to RT. Clk on all partitions and if given the option to unmount, go ahead and unmount.  For swap, use SWAPOFF
3.  Without knowing what sda2 is or holds, decide on how much space you want to take from sda2 (at the moment).  Remember that it will count in mb and not GB (1000mb = 1GB).
-  Rt. Clk on sda2 and select RESIZE.  Grab the right-hand side/arrow and shrink to what you've decided.
-  Rt. Clk. on the extended partition and grab the left side to enlarge .. taking up the space vacated
-  select sda5 and also enlarge (grab the left side and slide left)
- Leave SWAP there.
4.  Review and apply.

*EDIT : just noticed drs305's post.  You can do that too if you decide to let go of sda2 totally.*

BACK UP files first (even windows' files).  There are no gurantees.

Good luck.

---

### Post by felinoel on 2009-07-19
> **drs305 said:**
> Do it from the LiveCD, make sure the linux and swap partitions are not mounted (sda5 and sda6). Do this by selecting the  partitions and then Partition, Unmount or Swapoff if you see that option. 

Are you able to select sda3? You can't click on it, you have to select its line from the botton section.

I am on LiveCD, but sda6 has some keys next to it, I am guessing that means it is mounted? Will use Partition, Unmount, or Swapoff to unmount

---

### Post by felinoel on 2009-07-19
> **raymondhenson said:**
> BACK UP files first (even windows' files).  There are no gurantees.

Good luck.Already lost all my files when I first tried to dual boot, but this is the second try (and it worked this time) and there is nothing to lose anymore so I'm fine

---

### Post by felinoel on 2009-07-19
> **drs305 said:**
> Based on the snapshot, here is one way to fix the problem, although a reinstall may be just as fast. Did ubuntu even start? It's possible it didn't even install all of the system files. If that is the case you should reinstall, although you can make the partitions first to prevent the same thing from happening again.

From the LiveCD:
1. Shrink or delete sda2 (before deleting, make sure you have no data in it).
2. Expand sda3 (extended partition). You have to select it from the bottom part of gparted, then "Resize" and drag it all the way to the left until it touches Windows (sda1).
3. Expand sda5 (linux). Select it, then Partition, Resize and drag it all the way to the left. Your linux / partition will now be approximately 276GB.
4. Once you have done all that, you can split off some of the linux partition's right side if you want to create a data partition or some other partition(s).Ok, now this worked, am now applying

---

### Post by felinoel on 2009-07-19
Seems to be working, thanks all

---

### Post by raymondh on 2009-07-19
Congratulations =D>

Happy Ubuntu-ing.

---

### Post by spooner_ on 2009-08-04
Hi all, 

I didn't want to start a new thread as my problem is very simliar to this one; I installed ubuntu but my partition size was 10gb and it still tells me that there's not enough space on / what can I do?

> Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3    9.4G  9.0G     0 100% /
tmpfs        tmpfs    1.4G     0  1.4G   0% /lib/init/rw
varrun       tmpfs    1.4G  108K  1.4G   1% /var/run
varlock      tmpfs    1.4G     0  1.4G   0% /var/lock
udev         tmpfs    1.4G  168K  1.4G   1% /dev
tmpfs        tmpfs    1.4G  480K  1.4G   1% /dev/shm
lrm          tmpfs    1.4G  2.7M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs    1.0M   36K  988K   4% /tmp
/dev/sda1  fuseblk    214G  167G   47G  79% /media/Optimus Prime
 

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bda9ec2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27851   223713126    7  HPFS/NTFS
/dev/sda2           29158       30401     9988096    7  HPFS/NTFS
/dev/sda3           27852       29157    10490445    5  Extended
/dev/sda5           27852       29096    10000431   83  Linux
/dev/sda6           29097       29157      489951   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by drs305 on 2009-08-04
> **spooner_ said:**
> Hi all, 

I didn't want to start a new thread as my problem is very simliar to this one; I installed ubuntu but my partition size was 10gb and it still tells me that there's not enough space on / what can I do?

I wrote a guide on lost "free space". It's the link "DiskSpace" in my signature line. 9GB should be large enough for / *if* you aren't storing large amounts of data and regularly clean out downloaded files.

You can start by clearing out downloaded .deb files, which can be downloaded again if necessary:
```

sudo apt-get clean
sudo apt-get autoclean

```

I'd take a look at the guide and run the commands or use the GUI apps to see what is taking up the space. If you have any questions, post back here.

Probably the first command to run to see which directory is taking up the most space:
```

sudo du --max-depth=1 -h / 

```

The most likely causes are unemptied trash, backups made to the wrong partition, and large log files. The guide will help you sort it out. For a 9GB partition, you might just have too much data on the system partition.

---

### Post by michy99 on 2009-08-04
You will have to either delete some things, or expand your Ubuntu partition. If you want to expand your partition, here is a good guide:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by spooner_ on 2009-08-04
Thank you for your quick replies!

it was my trash! it wasn't clean, I tried to empty it but it would fail. So I restored and deleted from home. 

Cheers!
**[B][COLOR=DarkRed][/COLOR]**[/B]

---

