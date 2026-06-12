---
title: "Ownership external HD can't be changed - read only on other systems"
date: 2009-07-17
forum: General Help
---

### Post by Mzwo on 2009-07-17
hi,

i ran into a few problems with a newly purchased external hd. 

firstly, owner seems to be root. which cannot be changed. even as root!
secondly, when hooking the hd up to my mac (which i need for professional purposes), it's recognised as read only. 

how can i become the rightful owner of my hd (who is this root guy anyway ;-) ) and how do i make it read and write for the mac?

i should add that i have not done anything to the filesystem or formatted the hd prior to use. out of the box, plug in the power, and go. i have hence no idea which filesystem is currently in use. nor do i know how to find out. which filesystem is suitable for linux and mac, by the way?

help much appreciated.

running 9.04 and osx 10.5 respectively.

cheers,

mzwo

---

### Post by Mzwo on 2009-07-19
bump.

sorry to insist, it's a little urgent.

i have tried searching the forum, with limited success. 

thanks,
mzwo

---

### Post by ugm6hr on 2009-07-19
If you did not format the HD yourself, this is very unusual.

Most HDs come as FAT32 (if they are advertised as Mac and MS suitable) or NTFS for Windows-only.

As far as I know, FAT32 & NTFS do not have ownership issues.  So how it could be root only is a bit surprising.

Perhaps plug it in and post the output from:
```
sudo fdisk -l
```

---

### Post by Mzwo on 2009-07-19
hi,

did that. output as follows:

```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab9efeaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        6271    48828125    7  HPFS/NTFS
/dev/sda3            6272       36481   242661825    5  Extended
/dev/sda5           24508       35988    92221101   83  Linux
/dev/sda6           35989       36481     3959991   82  Linux swap / Solaris
/dev/sda7            6272        7121     6827562   82  Linux swap / Solaris
/dev/sda8            7122       24507   139653013+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x0031a3d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2    31008256   976760032+   7  HPFS/NTFS
```



what to do - format? it should be read and write for ubuntu and mac.

thanks,

mzwo

---

### Post by rudi009 on 2009-07-19
this happened with my psp yesterday.suddenly it went "read-only"!! I formatted..If data is not too much to back up format it..why waste time..It's good for knowledge though and I'm also waiting for someone to answer..:o

---

### Post by ugm6hr on 2009-07-19
Apparently, I was wrong:
[http://www.mkssoftware.com/docs/man1/chmod.1.asp](http://www.mkssoftware.com/docs/man1/chmod.1.asp)

NTFS do recognise permissions, but allows all files / directories to be read / execute.

I am uncertain what the most appropriate file format for Mac / Ubuntu sharing would be.  FAT32, perhaps?

Maybe try asking in the Mac subforum.

---

### Post by Mzwo on 2009-07-19
thanks.

i'm prepared to go trial and error on mac compatibility. how do i go about formatting in FAT32 or NTFS respectively? boot up vista?

cheers,

mzwo

---

### Post by ugm6hr on 2009-07-19
FAT32 has a 4GB per file max size, so can cause problems from that viewpoint.  However, it is universally compatible with everything.

NTFS is a MS format, but is also well-supported by Linux.

I have seen some HFS+ How-tos for Ubuntu; HFS+ is the OSX format (I think).

Try formatting in OSX and see what options it gives you.  Then google those formats for Ubuntu.

---

### Post by Mzwo on 2009-07-19
cheers. will try.

mzwo

---

