---
title: "Backup Software"
date: 2011-03-11
forum: General Help
---

### Post by barnesy on 2011-03-11
Hi Guys,
I'm looking for a way to set up a backup with two 2TB hard drives.  

What I want to do is basically mirror two drives.  What ever I copy to the one drive I want it to be "cloned" with the other drive.

Is there any software that could help me with this?

Does anyone know of a better to do something like this?

Thanks for the help!

---

### Post by Frogs Hair on 2011-03-11
This may be worth looking at.[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by vanadium on 2011-03-11
rsync will probably be more what you are looking for. It can mirror a directory structure. When it runs, it only updates files that have changed in the source, so an update is very fast. You can therefore very regularly update your mirror copy.

Making an image, in contrast, takes a long time. You do not want to do that very regularly.

---

### Post by ElSlunko on 2011-03-11
I use backintime to backup every hour.

---

### Post by barnesy on 2011-03-11
Thanks for the help.

rsync might be what I am looking for.  I don't need to make an image.  I just want to basically use one of the drives as my main storage but at the same time it is mirrored with another drive(just in case one of the drives fails.  I want to be safe).  

I tried to set up a Raid1 using the BIOS but for some reason I can not get it working.  I have it set properly in the BIOS and it says that is working but I think the issue might be in Ubuntu.  Would this be the way I want to do it if I can get it working?  Is it possible to do?  I have an ASUS A8N-SLI.


Thanks again for the help!

---

### Post by smashingpumpkin on 2011-03-11
I've you were trying to set up up hardware RAID via your BIOS,
then the issue can not be in Ubuntu.

If it's hardware RAID 1, then whatever you write on hard hdisk 1 will also be written on hard hdisk 2.
The hardware raid will not care what os you are running,
it will not care what kind of data is on the disks,
it will just make sure tht every file exists double, once on hdisk 1, once on hdisk 2

If you have 2 hard disks in your pc,
and you set up raid 1,
when installing ubuntu (or any other os), only 1 disk will visible.
In the background everything will be written in a mirrored way on the 2 disks.

rsync would aslo be an option, but it's quite different:
- RAID 1: your OS sees one disk
  every file is physically always on two disks.
  if you make a new file, it is on the 2 disks immediately.
- without raid 1 an dwith rsync
  -> your OS sees 2 disks
  -> when you create a new file, it only exists on one disk,
      until you decide to run rsync, which will copy all new files that do not exist yet to the second disk.

From what you describe above, it sounds like RAID 1 is more what you would want?

---

### Post by barnesy on 2011-03-11
> **smashingpumpkin said:**
> I've you were trying to set up up hardware RAID via your BIOS,
then the issue can not be in Ubuntu.

If it's hardware RAID 1, then whatever you write on hard hdisk 1 will also be written on hard hdisk 2.
The hardware raid will not care what os you are running,
it will not care what kind of data is on the disks,
it will just make sure tht every file exists double, once on hdisk 1, once on hdisk 2

If you have 2 hard disks in your pc,
and you set up raid 1,
when installing ubuntu (or any other os), only 1 disk will visible.
In the background everything will be written in a mirrored way on the 2 disks.

rsync would aslo be an option, but it's quite different:
- RAID 1: your OS sees one disk
  every file is physically always on two disks.
  if you make a new file, it is on the 2 disks immediately.
- without raid 1 an dwith rsync
  -> your OS sees 2 disks
  -> when you create a new file, it only exists on one disk,
      until you decide to run rsync, which will copy all new files that do not exist yet to the second disk.

From what you describe above, it sounds like RAID 1 is more what you would want?

Great thanks for the info!  

Is there anyway to test to make sure that the RAID1 is actually working?

What would happen if my motherboard died? Could I move the two drives to another computer to get the data off of them(then set up another RAID1 with a new board?)

I tried to take one of the drives and put it in another computer to see if I could see what was on it and that wouldn't work.  I'm thinking the BIOS formats the second drive(the one I can't access in Ubuntu) a certain way that only the BIOS can read.  

Thanks again guys. I really appreciate the help!!

---

### Post by smashingpumpkin on 2011-03-11
Hehe, to be absolutely sure your RAID 1 works
-> power off
-> take disk 1 out
-> power ON and see if he boots up, and you can access your data
-> power off
-> insert disk 1 again
-> remove disk 2
-> power ON and see if he boots up, and you can access your data

haven't tried this myself, but that's how I would test to make sure that it works :lolflag:



also, **I think** you should be able to take one of the 2 drives, and put it on another computer or an external hard drive enclosure and read your data that way.

how exactly did you try this when you put this disk in another computer to read your data?
-> did you add the removed the disk as a secondary disk in the other computer and tried to read it via the   other computer's guest os?
-> or did you put the removed disk in the other computer as primary disk and tried to boot straight of this disk?
-> or something else?

---

### Post by barnesy on 2011-03-11
> **smashingpumpkin said:**
> Hehe, to be absolutely sure your RAID 1 works
-> power off
-> take disk 1 out
-> power ON and see if he boots up, and you can access your data
-> power off
-> insert disk 1 again
-> remove disk 2
-> power ON and see if he boots up, and you can access your data

haven't tried this myself, but that's how I would test to make sure that it works :lolflag:



also, **I think** you should be able to take one of the 2 drives, and put it on another computer or an external hard drive enclosure and read your data that way.

how exactly did you try this when you put this disk in another computer to read your data?
-> did you add the removed the disk as a secondary disk in the other computer and tried to read it via the   other computer's guest os?
-> or did you put the removed disk in the other computer as primary disk and tried to boot straight of this disk?
-> or something else?


Well I took out one of the drives(the one that I couldn't access through Ubuntu and should be a mirror of the other drive) and put it in an external enclosure.  I then hooked it up to my Windows 7 box and it just saw it as a unformatted drive.  I was not able to see if anything was actually on it.  It wanted me to format it before I could use it.  That concerned me because I assumed it wasn't working and if it was working I then thought "what if the motherboard died and I need to hook this drive up to another PC to retrieve the data?"

---

### Post by smashingpumpkin on 2011-03-11
Did you go into administrative tools -> disk management on windows 7?

Your linux partitions are probably ext3 or ext4 ?

Windows 7 can not read ext3 of ext4, so you will never be able to read the data with windows 7 (unless maybe with some special tools/drivers)

But the disk management of windows will indicate the partitions on the disk if they exist.

When you opened the disk management tool:

- Did it show a partition or multiple partitions (it will say something like "Primary (healthy)", the size o the partition(s) will be indicated, but there will be no drive letter for that partition(s) and you can not do anything with it(them) under windows
=> in this case it's probably okay with your RAID1 setup
=> you could boot the server from a linux boot cd instead of
     from windows 7 and read your data that way

- Or did it show "Unallocated"
  => in this case there are really no partitions on the hard drive 
        and the RAID 1 is not functioning.

---

### Post by barnesy on 2011-03-11
> **smashingpumpkin said:**
> Did you go into administrative tools -> disk management on windows 7?

Your linux partitions are probably ext3 or ext4 ?

Windows 7 can not read ext3 of ext4, so you will never be able to read the data with windows 7 (unless maybe with some special tools/drivers)

But the disk management of windows will indicate the partitions on the disk if they exist.

When you opened the disk management tool:

- Did it show a partition or multiple partitions (it will say something like "Primary (healthy)", the size o the partition(s) will be indicated, but there will be no drive letter for that partition(s) and you can not do anything with it(them) under windows
=> in this case it's probably okay with your RAID1 setup
=> you could boot the server from a linux boot cd instead of
     from windows 7 and read your data that way

- Or did it show "Unallocated"
  => in this case there are really no partitions on the hard drive 
        and the RAID 1 is not functioning.


The drive said "Unallocated"

The BIOS indicates that the RAID 1 is "Healthy" though.

I'm going to try this:
Reconfigure the RAID 1 again.
Once in Ubuntu format the drive(NTFS) then copy some files to it.
Power down then remove the other drive and put it in an enclosure and see if I can access it with my Windows 7 PC.

This should indicate if the RAID 1 is working properly right?

Thanks!

---

### Post by TimEnid on 2011-03-11
i have a questions re this:
So what i plan to do is swap my 3.0gb/s internal to a 6.0. I want to  install a new ubuntu OS (same as im using now, 10.10) but dont want to  reinstall all my apps manually. I want to be able to do a restore and  have all the apps that i currently have, restored to my pc after i  install the new OS. Is there a better method for this? i dont want to clone my current hd, because i want to start the OS fresh.

---

### Post by The End of The World on 2011-03-11
I would install [remastersys]("http://remastersys.sourceforge.net/remastersystool.html"). This will make a backup of your computer into a LiveCD image - so it's a bootable backup. 
Hope it helps! :D

Definition of Remastersys, according to their site: > It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.

---

### Post by barnesy on 2011-03-11
> **barnesy said:**
> The drive said "Unallocated"

The BIOS indicates that the RAID 1 is "Healthy" though.

I'm going to try this:
Reconfigure the RAID 1 again.
Once in Ubuntu format the drive(NTFS) then copy some files to it.
Power down then remove the other drive and put it in an enclosure and see if I can access it with my Windows 7 PC.

This should indicate if the RAID 1 is working properly right?

Thanks!


Okay so I tried this method and Windows sees the drive as "Unallocated" space.  

What am I doing wrong?  Is there a certain way I have to format the drive in Ubuntu so this works?

Thanks!

---

### Post by CoolJohnB on 2011-03-11
I use luckbackup which is a graphical interface for rsync and works very well

---

### Post by barnesy on 2011-03-11
> **CoolJohnB said:**
> I use luckbackup which is a graphical interface for rsync and works very well


I will try it out since I can't seem to get the RAID 1 working through my BIOS.

Does this software just copy data from one hard drive to another?

Am I still able to use either of the drives on another computer(running windows or any of OS?)

Thanks!

---

### Post by tordeu on 2011-03-11
I have cloned drives as well and do NOT use RAID for various reasons. To clone two drives with rsync is really easy.

If the two drives are mounted and the source is /media/source the the destination is /media/destination, all you need is:

```

sudo rsync -av --del /media/source/ /media/destination/

```

I am calling it manually (I put the line in a script named clone.sh) at the end of the day (because, if I accidentally delete a file it is still on the second drive), but you could use cron to let it run manually once an hour or something like that.

---

### Post by barnesy on 2011-03-12
> **tordeu said:**
> I have cloned drives as well and do NOT use RAID for various reasons. To clone two drives with rsync is really easy.

If the two drives are mounted and the source is /media/source the the destination is /media/destination, all you need is:

```

sudo rsync -av --del /media/source/ /media/destination/

```I am calling it manually (I put the line in a script named clone.sh) at the end of the day (because, if I accidentally delete a file it is still on the second drive), but you could use cron to let it run manually once an hour or something like that.


Thanks for this.  This is exactly what I want to do.

I will test this out today.

Thanks again!

---

