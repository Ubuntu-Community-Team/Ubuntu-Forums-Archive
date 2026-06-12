---
title: "Partitioning an SD Card *Help"
date: 2009-10-17
forum: General Help
---

### Post by sendblink23 on 2009-10-17
I want to format my SDHC 32gb card into 2 fat32 partitions 
1st parttion: 4.5gb
2nd partition: All the rest that's left

Tried using Partition Editor from Ubuntu LiveCD (9.04), but always the second partition has an error icon after finishing processing the partitioning, it comes out like an unrecognized partition.

I plan to use it for windows.

Could anybody help me out on making this work?

Thanks

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> I want to format my SDHC 32gb card into 2 fat32 partitions 
1st parttion: 4.5gb
2nd partition: All the rest that's left

Tried using Partition Editor from Ubuntu LiveCD (9.04), but always the second partition has an error icon after finishing processing the partitioning, it comes out like an unrecognized partition.

I plan to use it for windows.

Could anybody help me out on making this work?

Thanks
Does an SD card have a partition table that supports such a thing? I am not sure that it does, but correct me if I am wrong.

---

### Post by rb0171610 on 2009-10-17
[http://geeks.pirillo.com/profiles/blogs/how-to-partition-an-sd-card](http://geeks.pirillo.com/profiles/blogs/how-to-partition-an-sd-card)
Here is a tutorial that someone once wrote.  It says that Windows will only see the first partition.  Linux can see them all.  
I would suggest using the command line to do the partitioning if you keep getting the errors.

---

### Post by sendblink23 on 2009-10-17
I read around allot that its possible to make partitions on to SD cards, but I haven't gotten it to work.. since I'm really bad with terminal commands...  that's why i only tried on Gparted GUI ..  so I ask here for those *Terminal GURU's for the extra help

That I know off, my SD card is mounted at /dev/sdf1

By the way I said clearly the Second Partition in Gparted has an Error Icon... so that tutorial, no where it mentions of that error.. and I did follow that Guide..in which its an obvious way to partition any Drive in Gparted...  so what I'm saying the Second partition its not even being recognized in Linux, only the First one is recognizable & usable

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> I read around allot that its possible to make partitions on to SD cards, but I haven't gotten it to work.. since I'm really bad with terminal commands...  that's why i only tried on Gparted GUI ..  so I ask here for those *Terminal GURU's for the extra help

That I know off, my SD card is mounted at /dev/sdf1
first thing, type man fdisk and read about the command
next, a little guidance :
fdisk is started by typing (as root) **fdisk *device*** at the command prompt something like /dev/hda or /dev/sda. The basic fdisk commands you need are:  
pprint the partition table   
ncreate a new partition
d delete a partition
q quit without saving changes
w write the new partition table and exit

 Changes you make to the partition table do not take effect until you issue the write (w) command.

---

### Post by sendblink23 on 2009-10-17
I'll give it a try now *thnx ;)

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> I read around allot that its possible to make partitions on to SD cards, but I haven't gotten it to work.. since I'm really bad with terminal commands...  that's why i only tried on Gparted GUI ..  so I ask here for those *Terminal GURU's for the extra help

That I know off, my SD card is mounted at /dev/sdf1

By the way I said clearly the Second Partition in Gparted has an Error Icon... so that tutorial, no where it mentions of that error.. and I did follow that Guide..in which its an obvious way to partition any Drive in Gparted...  so what I'm saying the Second partition its not even being recognized in Linux, only the First one is recognizable & usable
Don't "obvious" and "clearly" me.  I am here to help you.  I am simply trying to offer you a tutorial at first glance.  I did not read it.  I glanced through it.  It is up to you to read it to make sure that you followed it correctly.
Secondly, you will need to make the effort to understand how fdisk works. Once you have "clearly" done that, make then "obviously" your next step would be to write another post if you cannot figure it out on your own and someone will point you in the right direction.
Good Luck.

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> I'll give it a try now *thnx ;)
you are most welcome.

---

### Post by sendblink23 on 2009-10-17
Do you have any idea what shall I insert when it mentions:

First cylinder (1-4078, default 1):   

?

I started with 
sudo fdisk /dev/sdf1
n  - new partition
p  - primary partition
1  - partition number

then it gave that question above

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> Do you have any idea what shall I insert when it mentions:

First cylinder (1-4078, default 1):   

?

I started with 
sudo fdisk /dev/sdf1
n  - new partition
p  - primary partition
1  - partition number

then it gave that question above I believe try hitting enter to accept the default.  You want to start with the first cylinder for the first partition.

---

### Post by rb0171610 on 2009-10-17
[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)
This may help some, just to make sure you are on the right track. (Note: Once you create the partitions, you will have to format them with fat32.)

---

### Post by sendblink23 on 2009-10-17
did *Enter, I'm really lost here:

Last cyliner, +cylinder or +size{K,M,G} (1-4078, default 4078):


=P pretty sure I'm gonna keep asking 1 by one.. on the one's I don't understand what it means

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> did *Enter, I'm really lost here:

Last cyliner, +cylinder or +size{K,M,G} (1-4078, default 4078):


=P pretty sure I'm gonna keep asking 1 by one.. on the one's I don't understand what it meansOk the M G refers to Megabbytes or Gigabytes.  You can pick a size rather than cylinder.  If you were to hit enter here, it would pick the last cylinder and create one partition of 32GB. So try entering a number followed by G and then enter. :P

---

### Post by sendblink23 on 2009-10-17
Ok I just saw your above posted link.. I'll try to follow his example to see how I can do what I want

Thank You very much

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> did *Enter, I'm really lost here:

Last cyliner, +cylinder or +size{K,M,G} (1-4078, default 4078):


=P pretty sure I'm gonna keep asking 1 by one.. on the one's I don't understand what it means
I knew that I had a 1.2Gb drive, but now I really know: 64 * 63 * 512 * 621 = 1281982464 bytes. I decide to reserve 128Mb of that space for swap, leaving 1153982464. If I use one of my primary partitions for swap, that means I have three left for ext2 partitions. Divided equally, that makes for 384Mb per partition. Now I get to work.  [COLOR=#000000]Command (m for help): **n**
Command action
   e   extended
   p   primary partition (1-4)
**p**
Partition number (1-4): **1**
First cylinder (1-621, default 1):**<RETURN>**
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-621, default 621): **+384M**
[/COLOR]you can see what this person entered above +384M, He hit <return to start the partition at the first cylinder, and he wanted a 384MB partition, so the last cylinder of the partition (or end of this partition) he typed +384M.  If you wanted to create an 8GB partition for example, you could try typing +8G and hitting enter.

---

### Post by sendblink23 on 2009-10-17
okay I made both partitions 
1st.   5gb
2nd.   to use the rest of the cylinder like you said *press Enter and it would use whats left as partition

now... what shall I do... just use: w   and  I would be done(then formatting each)?

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> Ok I just saw your above posted link.. I'll try to follow his example to see how I can do what I want

Thank You very much
It is important that you figure this out on your own, I will help you but partitioning a disk and formatting it, especially a removable disk is good practice. So if you mess up or don't do it correctly (make the disk one partition instead of two) You can retry until you get it right. You can at least say you now know how to partition a disk from the command line.  It is not difficult, really.  Take your time, relax and enjoy the learning experience.
Note: most commands in Linux, type command_name --help, e.g. fdisk --help for a little info on how to run the command, type man command name to read the **man**ual on the command, e.g. man fdisk, and lastly, go to the internet and type command_name linux command line tutorial and read a few different tutorials to get a good knowledge of how the command works and what you can do with it, e.g. fdisk linux command line or partition a disk linux command line.

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> okay I made both partitions 
1st.   5gb
2nd.   to use the rest of the cylinder like you said *press Enter and it would use whats left as partition

now... what shall I do... just use: w   and  I would be done(then formatting each)?
;) I believe so, I am recalling from memory.  So try it.  and what do you think the w stands for?

---

### Post by sendblink23 on 2009-10-17
> **rb0171610 said:**
> ;) I believe so, I am recalling from memory.  So try it.  and what do you think the w stands for?

W I'm guessing it would be  *Write   ?


It gave me an invalid argument 22  

I'm guessing it won't work on this sd card...   like gparted's gui gave me...  I'm going to reboot and reinsert the sd card, to see if it did work just incase.. I know if I fail I can always reformat it & keep trying like you mentioned... and yeah I noticed when you mentioned the *man in the beginning it was like a manual.. so learned allot things here right now from you  Thnx

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> okay I made both partitions 
1st.   5gb
2nd.   to use the rest of the cylinder like you said *press Enter and it would use whats left as partition

now... what shall I do... just use: w   and  I would be done(then formatting each)?
mkfs -t vfat device_name
(hint: mkfs:make file system, -t for type)
on a typical drive, first partition is /dev/sda1 second is /dev/sda2
so if i wanted to format both partitions with FAT, i would type:
mkfs -t vfat /dev/sda1
mkfs -t vfat /dev/sda2
:P

---

### Post by rb0171610 on 2009-10-17
> **sendblink23 said:**
> W I'm guessing it would be  *Write   ?


It gave me an invalid argument 22  

I'm guessing it won't work on this sd card...   like gparted's gui gave me...  I'm going to reboot and reinsert the sd card, to see if it did work just incase.. I know if I fail I can always reformat it & keep trying like you mentioned... and yeah I noticed when you mentioned the *man in the beginning it was like a manual.. so learned allot things here right now from you  Thnx
At least now, you have an error from the command line that you did not get doing it with the GUI.  It is saying that writing these partitions to the partition table of the SD card is an invalid argument.  I am going to agree with you, I do not think that it supports multiple partitions, however it probably does.  I just wouldn't think to do that.

---

