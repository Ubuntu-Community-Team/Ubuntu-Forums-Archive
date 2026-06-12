---
title: "fix bad sectors using 12.04"
date: 2012-05-01
forum: General Help
---

### Post by IdanSuper on 2012-05-01
I'm using ubuntu 12.04 it there's a way to fix bed sectors using that? thanks.. I think that I have 6 bed sectors and I want my Ubuntu to ignore them..

---

### Post by Gyokuro on 2012-05-01
Hi

Bad sectors are indicators that your hard drive is physical damaged and therefore you should replace it - however if you like to live dangerous you have to use fdisk (umount the bad drive and then check the bad drive with fdisk). Backup your files as it's only a matter of time when the drive get really crazy.

---

### Post by IdanSuper on 2012-05-03
i'm with laptop and it's my main hard drive, the system on it.. how i can unmount the hard drive and fix it?

---

### Post by oldos2er on 2012-05-03
```
sudo touch /forcefsck
``` will cause fsck to be run at next boot. However, bad sectors are not fixable, and your hard disk itself will mark such sectors as unusable, up to a point. 

[http://en.wikipedia.org/wiki/Bad_sectors](http://en.wikipedia.org/wiki/Bad_sectors)

---

### Post by PeterP24 on 2012-05-03
a solution about fixing bad sectors depends on their location: would they be close to the end address of the hdd, you could partition your hdd in order that the second partition to contain all those bad sectors. Just my 2 cents from a problem I fixed 10 years ago. Since they are close to the end address of the hdd all you can loose is about 5GB storage of hdd ... . At the cost of not using those 5 Gb of storage and thus avoiding those bad sectors. But it really depends if they are close to the hdd end address.

---

### Post by dcstar on 2012-05-04
> **IdanSuper said:**
> I'm using ubuntu 12.04 it there's a way to fix bed sectors using that? thanks.. I think that I have 6 bed sectors and I want my Ubuntu to ignore them..

```
man badblocks
```

---

### Post by Herman on 2012-05-04
In addition to what the above posters already suggested, there is an e2fsck command for dealing with bad sectors,
```
sudo e2fsck -c -c -k -v /dev/sda2
```or 
```
sudo e2fsck -cc -k -v /dev/sda2
```Where: the command should be run on a file system that is not mounted, and where /dev/sda2 is the partition containing the file system to be checked, if not then replace the device number with whatever is appropriate for your particular situation as shown by a partition editor.

I'm not sure if the '-c -c' version or the '-cc- version is correct, but it shouldn't hurt to try either one and see which one works. Maybe you can supply some feedback on which is best.

There are a number of different causes of damage to a hard disk, and whether or not the damage will get worse and the rate of deterioration will depend on what the main cause of the problem is. If it's a once-of accident like a head crash from mis-handling the spinning hard drive, then it's possible your hard drive won't deteriorate further unless the accident that caused the damage is repeated. Otherwise if the hard drive is dying because of a bad spindle bearing or losing the magnetic properties in the hard drive's surface then you're only postponing the inevitable and any improvement will be temporary at best. Generally, the best thing to do is go and buy a new HDD or an SSD ASAP if you value your data.

---

