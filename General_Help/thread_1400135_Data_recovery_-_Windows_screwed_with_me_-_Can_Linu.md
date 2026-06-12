---
title: "Data recovery - Windows screwed with me - Can Linux come to the rescue? :D"
date: 2010-02-06
forum: General Help
---

### Post by michellez on 2010-02-06
Hi Guys,

Can any one recommend any apps or have any ideas to help with the following? Yes Windows screwed us over but I'm hoping Linux can come to the rescue as I'm struggling! :( It's a mates PC - wish I could convert him to Linux! ;)

I'm sat here with a 32bit 9.10 live CD wondering how it can help.

PC with 2 hard drives in RAID 0 (stripped) - using onboard Nvidia chip.

3 partitons: XP (32bit) / Win7 (64bit) / Data - all NTFS.

Office 2010 beta was installed on the Win7 partition. It ran out of disk space though. After this the data partition has gone! (seen as unused space by Windows)

I downloaded the free Partition Wizard and the recovery mode can see the data partition that was there and does a simple list of data on it to confirm (if only it would let me copy it out!). If you try and recover it though it wants to screw with the Windows 7 partition.

To me it looks like the Windows 7 partition when it filled up has "ballooned" or something over the data partition - god knows how!!

I downloaded a trial of Ontrack Pro out of interest but that just doesn't show any partitions in Win7 (64bit and drivers maybe something to do with it?) and in XP it just crashes (32bit so no idea why it crashes).

I dabble in Linux but am struggling because of the RAID being 'software' and the headaches I've had with Linux and this before. No idea of any tools to help with Linux either.

I'm not too fussed about recovering the actual partition but just get the data off it and on to a USB HDD or across the network, that I can then copy back later after recreating a blank partition.

Thank you!
Shell

---

### Post by Leppie on 2010-02-06
you could check out testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
it can recover the partitiontable of a damaged partiton. along with testdisk comes photorec which can recover data files on corrupt partitions.
testdisk can alos access raids.
to install testdisk:
```
sudo apt-get install testdisk
```
to run testdisk:
```
sudo testdisk
```
to run photorec:
```
sudo photorec
```

---

### Post by 2hot6ft2 on 2010-02-06
You could use a livecd to mount the windows partition and copy whatever files you want off of it to back up what you can. Just browse to them like usual in Ubuntu.

---

### Post by Leppie on 2010-02-06
> **2hot6ft2 said:**
> You could use a livecd to mount the windows partition and copy whatever files you want off of it to back up what you can. Just browse to them like usual in Ubuntu.
not sure how the OP would mount an erased partition...

---

