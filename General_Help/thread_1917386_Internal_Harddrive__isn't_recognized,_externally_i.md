---
title: "Internal Harddrive  isn't recognized, externally it is"
date: 2012-01-29
forum: General Help
---

### Post by FaceTheDream on 2012-01-29
Hello,

I'm having an issue with my 3TB goflex desk, its formatted in NTFS and I have lots of information on there I just have no where else to put, so i can't reformat to FAT, or any other format. Regardless when it is mounted via USB using the enclousure, it works fine. Now I have another 1TB NTFS disk, and I used the NTFS Configuration tool, and i mean it asked for me password but no GUI or anything popped up, but now I just have to mount it, but it is seen. but the 3TB drive wont even show up as mountable when internal, it just shows up in the Disk Utility or gparted, both of which say the 2.5TB partition I have is 'free' while in reality its not. I've debated somehow backing it up, but I just don't have enough space for such an operation I just need to mount it internally so I can share the files between my network.

Thanks In Advance

FaceTheDream.

EDIT: After some tinkering around I have got NTFS Configuration tool to open.  But it still doesn't recognize my 3TB drive, but does indeed see my 1TB drive and the partitions on that drive.

---

### Post by dcstar on 2012-01-30
> **FaceTheDream said:**
> Hello,

I'm having an issue with my 3TB goflex desk, its formatted in NTFS and I have lots of information on there I just have no where else to put, so i can't reformat to FAT, or any other format. Regardless when it is mounted via USB using the enclousure, it works fine. Now I have another 1TB NTFS disk, and I used the NTFS Configuration tool, and i mean it asked for me password but no GUI or anything popped up, but now I just have to mount it, but it is seen. but the 3TB drive wont even show up as mountable when internal, it just shows up in the Disk Utility or gparted, both of which say the 2.5TB partition I have is 'free' while in reality its not. I've debated somehow backing it up, but I just don't have enough space for such an operation I just need to mount it internally so I can share the files between my network.

Thanks In Advance

FaceTheDream.

EDIT: After some tinkering around I have got NTFS Configuration tool to open.  But it still doesn't recognize my 3TB drive, but does indeed see my 1TB drive and the partitions on that drive.

Probably the hardware/software in the external enclosure addresses the drive differently than the internal connection.

---

### Post by FaceTheDream on 2012-01-30
Perhaps, but after trying to find its UUID to *mount it* because I can find it in both the Disk Utility & gparted, but they both say its 'free' but it obviously isn't. So I can't find the UUID, and It will recognize when I put the drive in the external drive. I've tried booting with both  IDE and SATA as the hard drive configuration in the BIOS just so I can see if that cleared anything up,  but it still hasn't.

---

### Post by oldfred on 2012-01-30
Was the drive ever in a RAID set as that saves meta data on a drive that interferes. Also gparted/Linux sometimes will not mount a NTFS partition that needs chkdsk. If one drive works and another does not then your BIOS settings should be ok. Is drive SATA or IDE/PATA. Jumpers on PATA drives can make a difference.

Gparted would not even show my XP disk and it took a long time before it showed my other drives. After chkdsk it showed all drives relatively quickly and Windows booted slightly faster.

---

### Post by FaceTheDream on 2012-01-30
Well the drive is part of a Seagate FreeAgent GoFlex Desk, so never. Its also a SATA,  all the drives excluding my DVD drive are Sata. chkdsk..so would I just run it under a Windows repair?

I mean the drive doesn't have anything but data, and whatever else that would usually be put there. I'll try chkdsk and post the results.

EDIT: So I ran it from the windows 7 disk, and It didn't get anywhere. Now here is something else I've noticed, my first partition of my 1TB drive wont mount automatically when booting Ubuntu will say - Failed to Mount  than the mount location. But it will mount after I try to use it in the NTFS Configuration Tool while the second partition won't mount gives me:

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /media/Download
mount failed

```Download is the First Partition, and I'm trying to mount the 2nd partition. NTFS Config also doesn't recognize the second partition but does the 1st. 

I'm just so confused on why this issue is occurring, usually I would be fine to reformat, but these two drives are the drives with sensitive information, and with all the old photos and stuff.

---

### Post by oldfred on 2012-01-30
I do not have a separate USB drive, but do have a 16GB flash drive with several partitions. When I plug it in, it auto mounts all the partitions which then prevent manual mounting until you unmount the auto mount that happened. The auto mount will often just show partitions as the size like 20GB.  I now try to label all partitions with gparted or Disk Utility so I have a better idea on what is where.

---

### Post by FaceTheDream on 2012-01-30
Okay, Gparted & the Disk Utility manager BOTH see it as FREE SPACE. I can't mount/unmount, or anything. The only function I can perform is a FORMAT, and I know for certain that the drive does have data and it is formatted in NTFS.

I have provided a picture for further clafication, I've run two commands:
```
mount
blkid

``` 
And you can see the what it results in, sdb is completely *unrecognized* as if its not there, but the second I plug it in via USB(externally) it works like a charm. The problem is that that's not practical especially since the usb controller keeps the disk running at full power all the time. 

EDIT: Partition 1 is just renamed of the sdb2 partition the smaller drive I cannot mount either.

---

### Post by oldfred on 2012-01-31
It is very strange that it works as USB but not otherwise. 

What does testdisk show? Since it works as USB I would not try using testdisk to reset anything.

Smart says it has a few bad sectors but it is green and that should mean it is ok.

---

### Post by FaceTheDream on 2012-01-31
Yeah, I'm currently moving all the contents of the drive to my Desktop HDD, which if all goes well will be the first step, and after than I'm going to reformat it, probably in FAT, or something recognizable by both Linux & Windows, and if the problem persists than I will need to look for another solution. 

OH ALSO, when I plugged the disk INTERNALLY on my desktop it WOULD NOT, read. So I have a feeling either Seagate might of put some sort of encryption or something? I honestly have no clue, but hopefully this reformat clears things up. So both systems won't read the drive internally.

Weird, 
Regardless Thanks for Everyone help, hopefully this problem will get resolved today.

FaceTheDream

EDIT:
I was reading about the drive and found this out "Internally the 3TB drive uses 512-byte sectors, however the GoFlex dock emulates a 4K drive to allow for a single 3TB partition to be created in Windows." - I'm curious if this would have caused an issue like this..probably not, but I mean still worth noting I think,

---

### Post by oldfred on 2012-01-31
Was it formated to gpt, or did using the 4k sectors make it sorta work under MBR in Windows.

Normally anything over 2TB or 2.2TIB needs to be gpt partitions as 2TB is the largest that MBR(msdos) works. Some have posted with MBR and Windows somehow wrapping around so only 2.2TIB was used, but it looked corrupted to Linux.

I do not fully understand all the 4k sector issues, more info:
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by FaceTheDream on 2012-01-31
Yeah, well it seems my only option at this point is to reformat it into GPT and than format it into FAT or ext4.

Now heres a question, if i format it into ext4, when someone  accesses the server from a windows machine using samba, will they be able to access the ext4 drive?

---

### Post by oldfred on 2012-02-01
Do not even consider FAT, use NTFS if necessary. FAT has no journal and cannot store files over 4GB.

I think with Samba it will work, but I do not use Samba nor really understand Samba.

---

### Post by FaceTheDream on 2012-02-01
Yeah well ext4 works. 

So I formatted to ext4 and a 100GB partition formatted in NTFS just incase, but they both work. And thanks for the heads up.

---

