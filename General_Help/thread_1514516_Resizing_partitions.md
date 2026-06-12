---
title: "Resizing partitions?"
date: 2010-06-21
forum: General Help
---

### Post by h4x0rmx on 2010-06-21
I have a 500GB HD that is partitioned in the following way:
```
/dev/sda1 ntfs ~160GB //Used for storage
/dev/sda2 ntfs ~170GB //Used for storage
/dev/sda3 ntfs ~115GB //Used for Windows OS
/dev/sda4 extended 15GB
     /dev/sda5 linux-swap 3GB
     /dev/sda6 ext4 12GB
```and I usually have connected a 2TB external HD that is used for storage.
Lately, I've been getting a message "*_The volume "Filesystem root" has only 5xx.xx MB disk space remaining_*"
I'm not really sure what that was referring to as the only thing that was getting close to 75% full was the external HD, but it wasn't close to having only 5xxMB left.
I was wondering what I can do to prevent this message from coming up again?
Also, no matter what was causing the problem, I DO want to resize my partitions.  I partitioned this HD when Ubuntu was not my primary OS and now I'd like to give Ubuntu a little bit more of space. Is there a safe way of resizing my partitions?
[I have set mounting points for my two ntfs partitions used for storage (done with the "NTFS Configuration tool"). I do want to keep those mounting points.]

---

### Post by bumanie on 2010-06-21
Assuming you can still boot into ubuntu please post the output of > df -h /

---

### Post by Mark Phelps on 2010-06-21
If you're using Vista or Win7, the "safest" way to resize their partitions is using their tool -- the Disk Management utility.

If you're running XP, you can do the resizing using GParted.

You should also use GParted to resize the Extended partitions and those inside it.

Best approach there is to use the GParted LiveCD.  You can download an image of one from distrowatch.com.

---

### Post by h4x0rmx on 2010-06-21
@bumanie
Here's the output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              12G   11G  607M  95% /
```

I can see there's a problem. How do I fix it? just resizing partitions?

@Mark Phelps
What are the steps to follow?
Shrink partitions in Windows (will Ubuntu still load?)
Then extend the size of the ubuntu partitions?

---

### Post by oldfred on 2010-06-22
Unless you are doing something special you have a lot of space in root?

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

Did you save a lot of data into home  or run a backup that wrote into root?

---

### Post by h4x0rmx on 2010-06-22
I resized all the NTFS partitions. In Ubuntu I tried to use GParted, but I couldn't resize the extended partition.  I thought on going back in Windows and format the unallocated space as a EXT 3 partition and see if that would help GParted (if not I was just going to boot with GParted live CD).
So I did format the unallocated space as EXT 3 and now my laptop won't boot. I get an error:
```
error: unknown filesystem
grub rescue>
```I think I just have to fix grub, but how would I do it?

Edit:
I just booted using a liveUSB and reinstalled grub.  I have Ubuntu back!!!
Now I need to figure out a way to resize the extended partition! :-\

---

### Post by h4x0rmx on 2010-06-22
I was trying to edit my partitions with Gpart, but it won't recognize the partitions.
I opened Ubuntu's Disk Utility and I can see my partitions.
What would you recommend to get GPart to work? Should I use another program?
I'm attaching a screenshot for reference.

Thanks!

---

### Post by dabl on 2010-06-22
You need to defrag the NTFS partitions before you resize them (or resize them again).  Boot Windows to "Safe" mode to do that (fewer running files that won't be defragged).

GParted can only do any action on _unmounted_ partitions.  for this, and other reasons I find it considerably more straightforward to boot a Parted Magic Live CD for this type of work: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by h4x0rmx on 2010-06-22
> **dabl said:**
> You need to defrag the NTFS partitions before you resize them (or resize them again).  Boot Windows to "Safe" mode to do that (fewer running files that won't be defragged).

GParted can only do any action on _unmounted_ partitions.  for this, and other reasons I find it considerably more straightforward to boot a Parted Magic Live CD for this type of work: [http://partedmagic.com/](http://partedmagic.com/)

It sounds like I'm going to have to reinstall grub again, is that the case?
I've already resized the NTFS partitions. I just need to resize the Linux partitions. I'll give Parted Magic live CD a try and report.

---

### Post by dabl on 2010-06-22
Grub does not care about partition sizes, only partition numbers.  As long as you don't change the number of partitions, grub will be OK.

---

### Post by h4x0rmx on 2010-06-22
> **dabl said:**
> Grub does not care about partition sizes, only partition numbers.  As long as you don't change the number of partitions, grub will be OK.

I guess I will have to reinstall grub, as I will get rid of the "tmp" (4.2GB) partition

Thanks!

---

### Post by h4x0rmx on 2010-06-22
I've tried using Parted Magic live CD, GParted live CD and Ubuntu liveUSB and ran GParted with the three systems.
All of them displayed my HD as one chunk of unallocated data.
I did unmount the partition before running GParted.  The weird thing is that I can boot up perfectly into Ubuntu and Windows.

What should I do? I'm still getting the message in Ubuntu saying that "The volume Filesystem root has only 6xxMB disk space remaining.
Any suggestions?

---

### Post by h4x0rmx on 2010-07-08
So I've managed to get GParted to work correctly, it now displays all the partitions.  See a screenshot @ [http://ubuntuforums.org/attachment.php?attachmentid=162793&stc=1&d=1278614028](http://ubuntuforums.org/attachment.php?attachmentid=162793&stc=1&d=1278614028)
I have those 5.88GB of unallocated space that I want to assign to my last partition /dev/sda6 ext4. I would combine the unallocated space with the extended partition and then resize until I get what I want, but I don't really know how to do it... the problem is that I already have 4 primary partitions so if I want to create a new partition with the unallocated space I get a message telling me just that, that I already have 4 primary partitions. Anyways GParted won't let me do anything on the extended partition. How else could I manage to merge the unallocated space with my ext4 partition?
Any help will be appreciated!

---

### Post by h4x0rmx on 2010-07-08
After getting GParted to display the right partitions, I just needed to swapoff to unlock the extended partition and be able to resize/move partitions around.

Thanks for your help!

---

