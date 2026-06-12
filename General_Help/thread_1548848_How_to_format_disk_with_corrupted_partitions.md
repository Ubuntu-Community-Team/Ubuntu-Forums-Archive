---
title: "How to format disk with corrupted partitions?"
date: 2010-08-09
forum: General Help
---

### Post by The Great Falcon on 2010-08-09
I got a 40GB seagate HDD which has got through some unsuccessful windows and linux installations and now all the partition tables are corrupted... I tried to format with System>Administration>DiskUtility but it gives this error when I'm do:
Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error
gParted was not even useful since it didn't not even detected the drive...

Isn't there any simple way to format the crap from the Ubuntu 10.04 Live CD??? I believe that on windows, there wouldn't be that problem since the "format c:" crap just format the drive without asking questions... All I want to do is to format the drive so I can create partitions later. Also, I have only access to the live CD and I don't have any Diskette drive installed... I believe we now live in a world where this crap isn't needed to fix a computer... ><

Anyway, I hope anyone have an answer for me and I'm waiting impatiently for it. Thanks

---

### Post by renkinjutsu on 2010-08-09
You can first wipe the partition table by doing something like ```
[COLOR="Silver"]sudo dd if=/dev/zero of=/dev/sdb[/COLOR]
[COLOR="Red"]and of course, replace /dev/sdb with the actual drive/devices name
Don't use this one.. use the one written below[/COLOR]
```

After doing that, fire up gparted.

---

### Post by chopinhauer on 2010-08-09
> **The Great Falcon said:**
> 
Isn't there any simple way to format the crap from the Ubuntu 10.04 Live CD??? I believe that on windows, there wouldn't be that problem since the "format c:" crap just format the drive without asking questions...

“format c:” would only format the first partition.

You have to partition your drive, even if you use only one partition. To do so you must choose “Format drive” (and not “Format volume”) in the Disk Utility, choose “MBR” as the partitioning scheme, and create one partition you can format later.

---

### Post by chopinhauer on 2010-08-09
> **renkinjutsu said:**
> 
```
sudo dd if=/dev/zero of=/dev/sdb
[COLOR=Red]and of course, replace /dev/sdb with the actual drive/devices name[/COLOR]
```


A
```

sudo dd if=/dev/zero of=/dev/disk_name bs=512 count=1

```
would be better (it doesn't overwrite the whole disk).

---

### Post by The Great Falcon on 2010-08-09
> **renkinjutsu said:**
> You can first wipe the partition table by doing something like ```
sudo dd if=/dev/zero of=/dev/sdb
[COLOR=Red]and of course, replace /dev/sdb with the actual drive/devices name[/COLOR]
```After doing that, fire up gparted.
Doesn't work... It outputs this:
```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: writing to `/dev/sdb': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00123326 s, 0.0 kB/s

```

Any manual solutions to format a disk? Jumpers thing no? Thanks!

---

### Post by Mister.Vash on 2010-08-10
Are you sure that the disk is located at /dev/sdb?

Issue the following command to verify it.
```
sudo lshw -C disk
```
 You'll want to look at the output from the 'Logical Name' to tell you where the system is seeing it.  Some additional details can be found here.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)


My guess is either the drive is not located at /dev/sdb, or if it is, then the drive may have a physical problem and that is why you saw the I/O error

---

### Post by The Great Falcon on 2010-08-10
> **Mister.Vash said:**
> Are you sure that the disk is located at /dev/sdb?

Issue the following command to verify it.
```
sudo lshw -C disk
``` You'll want to look at the output from the 'Logical Name' to tell you where the system is seeing it.  Some additional details can be found here.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)


My guess is either the drive is not located at /dev/sdb, or if it is, then the drive may have a physical problem and that is why you saw the I/O error
Here is what it outputs: (first is my working drive and the second is the one I wanna format... Note: Both are supposed to be SATA connected drives but only one is showing as so...)
```
  *-disk:0
       description: ATA Disk
       product: WDC WD5000AAKS-0
       vendor: Western Digital
       physical id: 0
       bus info: scsi@5:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WMAWF1392499
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=915247c6
  *-disk:1
       description: SCSI Disk
       physical id: 1
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       size: 37GiB (40GB)

```And what could be the "physical" error that you told about? It was working fine just before I screw up the partitions... I had windows and linux installed on it...

Thanks for help anyway :D

---

### Post by DeadlyOats on 2010-08-10
When I want to delete all of my partitions and recreate those partitions, I use the Windows XP install CD.  I Boot from the CD.  Then when I get to the install windows menus.  I choose to repair windows, then I choose to go to the command line interface.  I forget what the menu choice is exactly.

Alternatively, I use the Ubuntu install CD.  When I get to the menu choice to partition the hard drive, I delete all partitions, and recreate them as I need them.

That's the way I do it, and it works for me.

I hope this helps...

---

### Post by The Great Falcon on 2010-08-10
> **DeadlyOats said:**
> When I want to delete all of my partitions and recreate those partitions, I use the Windows XP install CD.  I Boot from the CD.  Then when I get to the install windows menus.  I choose to repair windows, then I choose to go to the command line interface.  I forget what the menu choice is exactly.

Alternatively, I use the Ubuntu install CD.  When I get to the menu choice to partition the hard drive, I delete all partitions, and recreate them as I need them.

That's the way I do it, and it works for me.

I hope this helps...
Trust me, I tried... With the XP formater, I select a partition and delete it and it freezes... On the linux partition creater, it says that there's an I/O error or something like that...

---

### Post by tshirtdr1 on 2010-08-10
Why would you want to format a bad disk drive? Even if you get it to work, your drive is bad and you will lose data. Buy a new hard drive. Hard drives are  the single most important piece of equipment in your system.

---

### Post by dabl on 2010-08-10
> **The Great Falcon said:**
> Doesn't work... It outputs this:
```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdb
dd: writing to `/dev/sdb': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00123326 s, 0.0 kB/s

```

Any manual solutions to format a disk? Jumpers thing no? Thanks!

Issue the dd command again, like this:

```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

If that returns errors, then you've got a fancy bookend.

---

### Post by The Great Falcon on 2010-08-10
> **tshirtdr1 said:**
> Why would you want to format a bad disk drive? Even if you get it to work, your drive is bad and you will lose data. Buy a new hard drive. Hard drives are  the single most important piece of equipment in your system.
Because it worked really fine just some time ago! Why would I replace a drive that runs nice?

---

### Post by The Great Falcon on 2010-08-10
> **dabl said:**
> Issue the dd command again, like this:

```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```If that returns errors, then you've got a fancy bookend.
Returns the same error as earlier I believe...
```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
dd: writing `/dev/sdb': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00138903 s, 0.0 kB/s

```

So, how was the drive wreck? Why has is broke if so? It was working really fine... All I did was to change the informations on the drive, right? So why would it die from that? I know a bit how the HDD work and in no way, there is a command "Scratch the disk with the reading head" or so... *rofl*
What's the problem? It's not even 2 years old I think... Still on Seagate's warranty you guys think?

---

### Post by dabl on 2010-08-10
> **The Great Falcon said:**
> 

So, how was the drive wreck? Why has is broke if so? It was working really fine... All I did was to change the informations on the drive, right? So why would it die from that? I know a bit how the HDD work and in no way, there is a command "Scratch the disk with the reading head" or so... *rofl*
What's the problem? It's not even 2 years old I think... Still on Seagate's warranty you guys think?

Too bad -- sorry. :cry:

A hard drive should last way longer than 2 years (but then, I buy Western Digital .....).  There's no way to really know what component failed, short of having a Seagate engineer spend the rest of the week running circuit diagnostics -- LOL.  Think of it like a lightbulb: "It worked fine yesterday -- what happened here?".

So, order up a nice WD hard drive, and get on with life!  :)

---

### Post by pbrane on 2010-08-10
What do you get with
```

sudo fdisk -l -u /dev/sdb

```

---

### Post by dabl on 2010-08-10
One final thought (last desperate attempt), check the data cable on the bad hard drive.  If you have another one of the correct configuration, then replace it.  A bad cable could produce the result that you are seeing.

---

