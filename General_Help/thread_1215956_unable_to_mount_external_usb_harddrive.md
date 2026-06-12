---
title: "unable to mount external usb harddrive"
date: 2009-07-17
forum: General Help
---

### Post by rudedcam on 2009-07-17
brand new 1.5 TB by default formated in NTFS.
when i fire it up, it does not mount on my laptop nor on my desktop (both using hardy). 
however, i have an other harddrive formated in ext2 which mount's perfectly.
I was able to mount the new harddrive on XP at first try (and unmounted safely too).
when I *lsusb*, my computer sees the harddrive.

could i get some help to mount it automaticaly when i start the beast?

formating it to ext3 is an option but that too i don't know how to do.

thanks folks

---

### Post by devosion on 2009-07-17
Before you format to ext3 try running...

> 
sudo fdisk -l


and post the output.

---

### Post by cariboo on 2009-07-17
I would suggest installing ntfsprog, it is in the repositories, the package consists of tools for dealing with ntfs partitions.

---

### Post by rudedcam on 2009-07-17
here are the results for *sudo fdisk -l*
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20c9a1da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    7  HPFS/NTFS
/dev/sda2            2434        3430     8008402+  83  Linux
/dev/sda3            3431        3929     4008217+  82  Linux swap / Solaris
/dev/sda4            3930       14593    85658580   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04a1b149

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS



as for ntfsprog package i cannot download it from the location my computer is trying to get if from. anybody knows how to retrieve the package from an other source? here's the error message:
> W: Failed to fetch [http://gulus.usherbrooke.ca/ubuntu/pool/main/l/linux-ntfs/libntfs10_2.0.0-1ubuntu2_i386.deb](http://gulus.usherbrooke.ca/ubuntu/pool/main/l/linux-ntfs/libntfs10_2.0.0-1ubuntu2_i386.deb)
  Could not connect to gulus.usherbrooke.ca:80 (206.167.141.10). - connect (113 No route to host)


W: Failed to fetch [http://gulus.usherbrooke.ca/ubuntu/pool/main/l/linux-ntfs/ntfsprogs_2.0.0-1ubuntu2_i386.deb](http://gulus.usherbrooke.ca/ubuntu/pool/main/l/linux-ntfs/ntfsprogs_2.0.0-1ubuntu2_i386.deb)
  Could not connect to gulus.usherbrooke.ca:80 (206.167.141.10). - connect (113 No route to host)



---

### Post by devosion on 2009-07-17
Here is a page for the deb file of ntfsprog for your distribution. Just click the link, then scroll down the second page for the download if your running 32 or 64 bit ubuntu. 

[http://packages.ubuntu.com/search?keywords=ntfsprogs]("http://packages.ubuntu.com/search?keywords=ntfsprogs")

I'd recommend before you start editing your fstab that you check to see if ntfsprog fixes your issues. The good news is that ubuntu is recognizing your external drive and is just a mount away.

---

### Post by rudedcam on 2009-07-17
i've sucessfully installed ntfsprog but i must not know how to use it because my problem is still not solved.

I can see the harddrive in Places>Computer  but it gives me a message error:
> Can't mount file

---

### Post by rudedcam on 2009-07-19
i have also tryed this:
```
sudo apt-get install ntfs-config
```

plus, i have installed ntfs-3g from the "synaptic package manager"

still no progress

---

### Post by rudedcam on 2009-07-20
```
 sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 294 not upgraded.

``````
 sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

```
unutbu wrote: > you may have to find a Windows machine into which you can plug your external HD. Then run "chkdsk /f" on the drive. Reboot Windows twice. Once you get Windows to recognize the drive, make sure you click the icon or buttons to make the drive "safe to remove". At that point, you should be able to recognize the drive in Ubuntu again.
[RIGHT][http://ubuntuforums.org/showthread.php?t=1122278]("http://ubuntuforums.org/showthread.php?t=1122278")[/RIGHT]
I did that, i even reformated the HD (in NTFS), whicj lead to the safe remouving of the HD. Back in Ubuntu, no luck.

c'mon guys, help me out! my situation is pathetic.

---

### Post by rocket16 on 2009-07-20
Why don't you format the Drive to ext3 using GParted? Then it will mount!

---

### Post by rudedcam on 2009-07-20
seriously, i've try that too! i have formated the thing with ext3 and then with ext2. still no luck!

---

### Post by rudedcam on 2009-07-22
i've updated to jaunty by updating this way
```
sudo update-manager -d
```
and formated to ext3. everything works like a charm!
however i had to change the rights from root to my user.
```
sudo chown -R username:username /media/drivename/ 
```

---

