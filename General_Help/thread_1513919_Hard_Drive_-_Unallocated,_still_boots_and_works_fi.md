---
title: "Hard Drive - Unallocated, still boots and works fine."
date: 2010-06-20
forum: General Help
---

### Post by SoFl W on 2010-06-20
I am not sure what is going on but the drive boots and seems to be working fine.  But take a look at the attached pictures.  The partitions are messed up, and gparted tells me the drive is unallocated. 

**df:**
```
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             34606040  25934324   6913808  79% /
udev                   1995128       284   1994844   1% /dev
none                   1995128       244   1994884   1% /dev/shm
none                   1995128       288   1994840   1% /var/run
none                   1995128         4   1995124   1% /var/lock
none                   1995128         0   1995128   0% /lib/init/rw
/dev/sdb3            336433328  27963800 291379688   9% /media/sdb3
/dev/sdb4            432557212  87693348 322891216  22% /media/sdb4
```**UNAME:** 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 02:41:03 UTC 2010 x86_64 GNU/Linux
Ubuntu studio 9.10

"sudo sh **boot_info_script055.sh**"  does not return any information. 

I have included pictures from palimpsest and gparted.  (The amount of space free is hysterical)   This didn't just happen, I was working on two other things but I don't want to confuse the issue with details that are irrelevant.  The second drive has "home" and "web", those partitions are not in use, my home folder is part of the first partition.

Is there something I can do to fix this?  (I thought I saw this once before but I am not hitting on the correct search terms)

---

### Post by NCLI on 2010-06-20
Your df looks just fine to me. Here's mine, for comparison:
```
root@NCLI-SERVER:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              53G  5,7G   45G  12% /
none                  2,0G  304K  2,0G   1% /dev
none                  2,0G     0  2,0G   0% /dev/shm
none                  2,0G  328K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/md0              4,1T  2,4T  1,7T  59% /home/seph/Media
/dev/sdd2             459G  291M  435G   1% /home/seph/Backup

```
If it works, don't mess with it. Just make sure to take a backup. If you're very bothered by it, take a backup and reinstall, reformatting the drive in the prcess. Looks like a partitioning error to me.

---

### Post by John Bean on 2010-06-20
> **SoFl W said:**
> I am not sure what is going on but the drive boots and seems to be working fine.  But take a look at the attached pictures.  The partitions are messed up, and gparted tells me the drive is unallocated. 

What does the output of "sudo fdisk -l /dev/sda" show? (the "-l" is lower case "L")

---

### Post by SoFl W on 2010-06-20
sudo fdisk -l /dev/sda
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           8        4380    35126122+   7  HPFS/NTFS
/dev/sda3               2        9726    78116062+   5  Extended
/dev/sda4            4381        5155     6225187+  83  Linux
/dev/sda5               2           7       48163+  de  Dell Utility
/dev/sda6            5156        9532    35158221   83  Linux
/dev/sda7            9533        9726     1558273+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by John Bean on 2010-06-20
I don't like the look of that at all. At least we can see what is confusing the GUI tools, there are overlapping partitions.

It can't have got in this state by itself, have you any clues about how it happened?

Anyway, I'd backup then see what testdisk makes of it. Or just put it down to experience and do a clean reinstall.

---

### Post by SoFl W on 2010-06-20
This happened because I work on these things when I am tired. The more I think about it  I had two separate problems and I thought they were one.  I am sure it happened when I tried to recover the Dell utility space from an old Avast backup... which I probably didn't need to worry about.  The other problem was a corrupt Windows system file on bootup.  

After I recovered the Del Utility, grub was corrupted,  I couldn't recover because of err15.  I followed [these instructions]("https://wiki.ubuntu.com/Grub2#Err15") to get it working again.  I am not sure if that caused problem, but I don't think so.  I am thinking it was the recovery of the dell partition.

---

### Post by John Bean on 2010-06-20
> **SoFl W said:**
> This happened because I work on these things when I am tired.

Been there, done that. I'm not being judgemental here, I was genuinely puzzled how it happened.

> I am thinking it was the recovery of the dell partition.

Very probably. Anyway, water under the bridge and all that.

This is now much clearer and I'm reasonably confident about a suggested path forward. Can you post the contents of your /etc/fstab?

---

### Post by jerome1232 on 2010-06-20
Overlapping? The I don't see any overlapping partitions, the only thing i see that's awesomely screwed up is there's a primary partition sitting inside an extended partition.

That's skill. The part that's in red, /dev/sda2 (a primary partition) should not be able to be within /dev/sda3 (the extended partition, contains logical partitions /dev/sda5+)

```
/dev/sda2   *           [COLOR="Red"]8        4380[/COLOR]    35126122+   7  HPFS/NTFS
/dev/sda3               2        9726    78116062+   5  Extended

```

---

### Post by John Bean on 2010-06-20
> **jerome1232 said:**
> Overlapping? The I don't see any overlapping partitions, the only thing i see that's awesomely screwed up is there's a primary partition sitting inside an extended partition.

Sloppy wording perhaps, but that's what I was referring to.

---

### Post by efflandt on 2010-06-20
The Dell recovery partition is also normally a primary partition sda1 (which would make sense based on its start and end).

So it looks like sda5 should be sda1, the bottom of extended partition sda3 should start at 4381, and sda6 and sda7 should be sda5 and sda6 respectively.  So in the end, it should end up looking like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2           7       48163+  de  Dell Utility
/dev/sda2   *           8        4380    35126122+   7  HPFS/NTFS
/dev/sda3            4381        9726    78116062+   5  Extended
/dev/sda4            4381        5155     6225187+  83  Linux
/dev/sda5            5156        9532    35158221   83  Linux
/dev/sda6            9533        9726     1558273+  82  Linux swap / Solaris
```[FONT=monospace]I would trust fdisk to do that by removing all and recreating corrected partitions with exact start and end points, but only after backing up anything you can still access and don't want to lose.  Doing that might confuse grub or the windows boot loader.  And I am not really sure if the Dell recovery partition was "converted" to a logical partition, or just has an incorrect partition number, because I do not know what changed it to sda5.

Deleting and recreating partitions exactly like they were does not delete data, as long as partitions are in the proper format for that type, and you do not format the partition.  But it is better to be safe than sorry (ie, back up first).
[/FONT]

---

### Post by jerome1232 on 2010-06-20
> **efflandt said:**
> The Dell recovery partition is also normally a primary partition sda1 (which would make sense based on its start and end).

So it looks like sda5 should be sda1, the bottom of extended partition sda3 should start at 4381, and sda6 and sda7 should be sda5 and sda6 respectively.  So in the end, it should end up looking like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2           7       48163+  de  Dell Utility
/dev/sda2   *           8        4380    35126122+   7  HPFS/NTFS
/dev/sda3            4381        9726    78116062+   5  Extended
/dev/sda[COLOR="Red"]5[/COLOR]            4381        5155     6225187+  83  Linux
/dev/sda[COLOR="Red"]6[/COLOR]            5156        9532    35158221   83  Linux
/dev/sda[COLOR="Red"]7 [/COLOR]           9533        9726     1558273+  82  Linux swap / Solaris
```[FONT=monospace]I would trust fdisk to do that by removing all and recreating corrected partitions with exact start and end points, but only after backing up anything you can still access and don't want to lose.  Doing that might confuse grub or the windows boot loader.  And I am not really sure if the Dell recovery partition was "converted" to a logical partition, or just has an incorrect partition number, because I do not know what changed it to sda5.

Deleting and recreating partitions exactly like they were does not delete data, as long as partitions are in the proper format for that type, and you do not format the partition.  But it is better to be safe than sorry (ie, back up first).
[/FONT]


Looks like you hit on it the nail (although the partitioning numbering should start with sda5 inside the extended partition) I second effiandt's suggestion.

---

### Post by SoFl W on 2010-06-20
Thank you for your suggestions, I will boot with my True Image, make a back up of everything and get to work.  I wanted to change things around and reinstall the Ubuntu side anyway, I just didn't want to mess with the Windows side.

---

### Post by John Bean on 2010-06-20
> **SoFl W said:**
> Thank you for your suggestions, I will boot with my True Image, make a back up of everything and get to work.  I wanted to change things around and reinstall the Ubuntu side anyway, I just didn't want to mess with the Windows side.

True Image is probably not a good choice given the state of the partition table. I'd be more inclined to use a file-by-file backup method.

I asked about fstab to check how partitions were being accessed; if they are mounted by UUID I'd suggest using testdisk to sort out the existing partitions with (probably) no loss of data, and the UUID will remain unchanged even if partitions are reordered.

I speak from experience here... and it worked well for me.

---

### Post by louieb on 2010-06-20
> **John Bean said:**
> I was genuinely puzzled how it happened.

I've seen the windows installer put a primary partition inside an extended one. There are a few partition tools such as Partition Magic for Windows and Disk Drake for Linux that will alter the partition table in a non-standard way.     

and command line tools such as fdisk and sfdisk have few edits and if you tell them - they will do it too.  

Even though the computer boots and works - Gparted  detects the non-standard partition and instead of trying to display a partition layout - it just shows a blank hdd.

---

### Post by SoFl W on 2010-06-20
Thanks for all your help and suggestions, I couldn't get any way to cheat and recover easily.  I had a few problems and nothing seem to work.  I was using a USB stick not a live CD.
I wanted to do a fresh install so I just convinced myself to do that.  At first I tried a straight Ubuntu install.  I set everything up and walked away.  When I returned it was on the live  CD desktop.  This struck me as odd, but I didn't watch it and I didn't  remember what happened after the last install.   When I rebooted there was a flashing underline cursor in the upper left and nothing else.

I then recovered my last full backup of the Windows partition which was before I installed 9.4, returning the state of my drive to what it was before I installed Ubuntu.  Ran all the windows updates, installed drivers for my new scanner/printer, some other software and was able to get everything up to date and looking nice, de-fragmented on the windows side.

I am not crazy about 10.4, so I tried to do an install of 9.10.  It told me there were no OS on the drive, but for some reason offered the opportunity to install 9.10 side by side.  (of what?) I didn't understand that so I did a manual install, it seemed to default on my second hard drive but I was careful and installed it on the first.  I wasn't paying close attention but I thought it finished at 75% and when to the live CD desktop.   I rebooted and it loaded Windows with no prompts.

Tried the process again, changing a few options and watching the install carefully.  It did stop at 75% and continued to the live CD desktop.  I rebooted and it went straight into Windows.  Now I figure my whole problem was with the USB image.
I downloaded 10.4 (this time) and burned the ISO to a CD, did an install, it seemed to work because here I am.  Slowly trying to get everything back to the way I liked it on my 9.10 install.  Still not crazy about 10.4.  

Thanks for your suggestions, I am not sure if the USB stick was the problem in the beginning of the recovery processes but in the end a reformat of the drive and a fresh install of Ubuntu is what I had to do. 

When I had openSUSE True Image would back up the linux (SUSE) partitions, it doesn't even recognize Ubuntu's partitions. I believe the True Image boot disk is linux based.  That was nice to do full backups of my dual boot system.

Thanks again for all your help.

---

