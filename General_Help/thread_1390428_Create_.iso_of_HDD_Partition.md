---
title: "Create .iso of HDD Partition"
date: 2010-01-25
forum: General Help
---

### Post by tom.swartz07 on 2010-01-25
Hi all,

Recently, Ive had some troubles with a drive and got it replaced. I did a clean install of Ubuntu and other things that I needed right away, but I still have the drive full of files that will be needed in the future.

Specifically, I have a Windows 7 Partition that Im not currently using, but I would like to preserve for when I upgrade my computer.


Is there any way that I could take this partition from the old drive and create an .iso file from it? The problem is- I need to take the .iso and- as its created- put it on an external drive.

Its a sizable partition, around 82 GB, and there's no room on said drive for the .iso to be placed, and the internal HDD wont be able to hold that kind of data either. 


Any suggestions on what I could do would be greatly appreciated!

---

### Post by bodhi.zazen on 2010-01-25
partimage will do this for you by breaking it into 4 Gb pieces, but you still need a place to store the images before burning to a CD / DVD.

---

### Post by Leppie on 2010-01-25
get a cheap external drive?

---

### Post by ajgreeny on 2010-01-25
82 GB even on DVDs will take a long time to make and burn, and how many DVDs would you need?

Surely the simplest way would be to get a cheap usb external drive and just copy the files/partition onto that.  You could zip the archive if you want, but a simple copy to a drive of even 100 GB would not take long and would be so very much quicker.

---

### Post by baddog144 on 2010-01-25
Guys. 
> Is there any way that I could take this partition from the old drive and create an .iso file from it? The problem is- I need to take the .iso and- as its created- put it on an external drive.

He's not suggesting that be put 82GB worth of data on DVDs. Just using an iso as a convenient method for holding the whole image. 

I would suggest using dd. There is a guide here: [http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd]("http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd")
Hope this helps ;)

---

### Post by ajgreeny on 2010-01-25
> **baddog144 said:**
> Guys. 


He's not suggesting that be put 82GB worth of data on DVDs. Just using an iso as a convenient method for holding the whole image. 


Well, I'm sorry if I got it wrong, but that is exactly what it seemed to me the OP was trying to do.  If not, I am baffled, and wonder what it is he does want.

---

### Post by ppirilla on 2010-01-25
I think you aren't quite asking what you want to ask.

An ISO image is useful for (and pretty much only for) burning CDs or DVDs.

You can create a disk image of a hard drive, as well, but they usually come in .img files.

---

### Post by tom.swartz07 on 2010-01-25
> **baddog144 said:**
> Guys. 


He's not suggesting that be put 82GB worth of data on DVDs. Just using an iso as a convenient method for holding the whole image. 

I would suggest using dd. There is a guide here: [http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd]("http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd")
Hope this helps ;)

Ive used dd to copy entire drives before, but how would i use it for just a specific partition to an .img? 

Im not particularly interested in the 3 other OS's (and respective partitions) on the drive, but I am particularly interested in ONLY the one partition.


Would I use something like this?
```
dd if=/dev/sda2 conv=sync,noerror bs=64K | gzip -c  > /path/to/external/drive/sda2.img.gz
```




I just want to be sure that I could archive this Partition until I need it again, then be able to restore it to an active partition for use (with relative ease)

---

### Post by baddog144 on 2010-01-25
That should be fine. Good luck!

---

### Post by tom.swartz07 on 2010-01-25
> **ppirilla said:**
> I think you aren't quite asking what you want to ask.

An ISO image is useful for (and pretty much only for) burning CDs or DVDs.

You can create a disk image of a hard drive, as well, but they usually come in .img files.

Thats correct, my mistake.

Thanks for all the help so far- Im just curious as to how to pipe dd through gzip just selectively using a specific partition.


Would I use something similar to 
```
dd if=/dev/sda2 conv=sync,noerror bs=64K | gzip -c  > /path/to/external/drive/sda2.img.gz
```

or would I use
```
fdisk -l -u /dev/sda
Outputs as:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16771859     8385898+  8e  Linux LVM
/dev/sda2        16771860    75489434    29358787+  8e  Linux LVM
/dev/sda3        75489435    75698279      104422+  83  Linux
/dev/sda4        75698280   117210239    20755980    5  Extended
/dev/sda5        75698343   117210239    20755948+  8e  Linux LVM
So to create an image of the second partition (sda2) from existing image of sda...

# dd if=/tmp/sda2.img of=/path/to/external/sda2.img bs=512 skip=16771860 count=$[75489434-16771860]
```


Additionally, will I need to create an empty file with that name, or will dd/gzip automatically make it as it outputs to it?

---

