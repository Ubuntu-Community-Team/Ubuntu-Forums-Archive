---
title: "Question about Partitioning"
date: 2010-06-14
forum: General Help
---

### Post by thefuturism on 2010-06-14
I'm very new to Ubuntu and have only used it a handful of times.

I'm trying to setup a my home theater PC with Ubuntu but I'm not sure about the partitioning.

Currently, I am running Windows 7 and I would like to install Ubuntu alongside it.

I was thinking about creating a large partition to store all my media files (music, video, etc) and having two other partitions (one for each OS). 

Would this type of setup allow me access to the media files from either OS? Ideally I'd like to be able to manipulate the files from Windows and view them on Ubuntu. 

Also, if this would work, what type of filesystem should the media partition be?

Thanks

---

### Post by Ryan Dwyer on 2010-06-14
Yeah, it all depends on the filesystem.

ext2/3/4 - native to Ubuntu but Windows won't read it without a 3rd party driver. Not recommended for your situation.
FAT - Read/write supported in both, but can't contain files larger than 4GB so if you have large movies this won't be an option.
NTFS - Read/write supported in both. Use this option.

---

### Post by thefuturism on 2010-06-14
Thanks for the information!

So my system should look like:

Partition 1 - Windows 7 (NTFS)
Partition 2 - Media Storage (NTFS)
Partition 3 - Ubuntu (ext2)

Or is it possible to run Ubuntu on a NTFS filesystem?

---

### Post by garvinrick4 on 2010-06-14
Windows and Linux can both read Fat32 and will show up in Windows as a J or K drive some letter and will show up in Linux as what-ever you Label it. So it shares music nicely.

Ready this will be a bit of info.
Take your Windows install and defrag a couple of times.

Put your ubuntu disk in and go to :Try Ubuntu"
Go to System/Administration to gparted. Open gparted
You will see your drive will be call sda
then your partitions will be sda1 and sda2 and so forth.
In windows they say C, D, E and so on in Linux sda1, sda2 and so on.

Now close that for me and open a Terminal by Applications to Accessories to terminal.

type this in there.

sudo fdisk -l    (that is a small L)

Now copy and paste that result to this thread and I will tell you how to make the partitions to
have what you need for your dual boot. Not that hard, just focus.

---

### Post by Ryan Dwyer on 2010-06-14
> **thefuturism said:**
> Thanks for the information!

So my system should look like:

Partition 1 - Windows 7 (NTFS)
Partition 2 - Media Storage (NTFS)
Partition 3 - Ubuntu (ext2)

Or is it possible to run Ubuntu on a NTFS filesystem?

The latest version of Ubuntu will use ext4, which is fine. Running Ubuntu on NTFS is not recommended, if not impossible.

---

### Post by thefuturism on 2010-06-14
I found the information you were after:


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbcd7a8cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2220    17825792   27  Unknown
/dev/sda2   *        2220        2233      102400    7  HPFS/NTFS
/dev/sda3            2233       60802   470456320    7  HPFS/NTFS

Disk /dev/sdb: 8023 MB, 8023703552 bytes
247 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      210485      226594   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(210484, 238, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(226593, 24, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       28267       78919   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(28266, 90, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(78918, 75, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      122082      247408   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(122081, 227, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(247407, 29, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      140265      140808     4161536    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(140264, 81, 19)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(140807, 203, 24)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

---

### Post by garvinrick4 on 2010-06-14
This will work if none of the files are over 4 gig. If they are have to do a different way.

Start out by defraging windows a couple of times. Is this a DELL computer? Let me see the
command
```

sudo blkid
```  small L

After defrag go into gparted in Live CD. Right click on sda3 and resize to what you want for Windows 7 left. The operating System is about 12 gig alone and I do not know how much you have in your personal files. What is left over you want to right click on and make a new Extended and format primary. Remember you have to check the green apply arrow to make gparted apply the command. Now right click on the Extended partition and make a new logical partiton and format it ext4 and about 10 gig and mount point is / Apply it, . Right click on extended again and make another new partition for the size you want the media. Make it formatted in Fat32 and label it media. If you have under 2 gig of Ram make a 3 gig or so swap partition if you are ok in Ram pass that. Ok remember which sda number they gave the 10 gig / that is going to be your operating system. 
  Go out of gparted and double click install, fill out the forms and then when you get to install page choose manual. Put your / which  gparted made for you / like sda5 most likely or whatever it is. Size is already done format to ext4 and no swap unless you are under 2 gig of ram, if are add a 3 gig of swap partition. When you get to last page will  you see a advanced tab in lower right open it and pick sda not sda5 or sda1, sda   . Now install.

 When done restart and give this command in a ubuntu terminal.

```
sudo update-grub
```If you look under places will be a partition named media and in windows it will be assigned a Letter.
 Put Ubuntu CD back in and go to gparted right click on your / or OS that is gave the 10 gig partition and label it what you want. Good idea if it is karmic koala name it karmic if
lucid lynx name it lucid. If you have to name media again right click on that partition and name it media, if it did not take first time.

---

