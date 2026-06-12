---
title: "Is there any hope for my files?. Please help!"
date: 2010-04-26
forum: General Help
---

### Post by JoeyF on 2010-04-26
I have an Emachine W3650.

I put in my Emachines restore disk(Giving this Desktop to a Friend and don't have time to get it working). Tried to see if it would work. It didn't get to the point where it formatted, Though. Just loading or something.

It gave me an error. So I took it out and restarted. Then GRUB said something like GRUB recovery. I can't remember. And it wasn't letting me boot into Ubuntu.


So I popped a Live CD and when I go to Computer, File System. It's just the Live CD contents. Not the actual Hard Drive files.


Is all of my stuff gone?(Surely it couldn't delete all of that that fast). Is there anything I can do?. It's detecting my Flash Drive just fine.

Note:I had Ubuntu on this and am trying to recover files from the LiveCD.



Sorry if this is choppy. It's really late and I'm sick to my stomach over this. 

:(

Thanks.

---

### Post by Grenage on 2010-04-26
Deep breath.... relax.

Is the local drive being listed at all?  If not, from the command line:

```
sudo fdisk -l
```

Double check it is being detected.  Assuming it is, try and mount it:

```
sudo mkdir /mnt/mydrive
sudo mount /dev/sd**XY** /mnt/mydrive
```

X and Y are obviously disk and partition numbers.  If it mounted ok, look in /mnt/mydrive and check for your files; if it didn't mount, tell us what it said.

---

### Post by mikewhatever on 2010-04-26
Linux live cds are not intended for recovering deleted data. If the data is intact and you just can't boot the system, it's a different story. For deleted files, testdisk is the tool.
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by JoeyF on 2010-04-26
> **Grenage said:**
> Deep breath.... relax.

Is the local drive being listed at all?  If not, from the command line:

```
sudo fdisk -l
```

Double check it is being detected.  Assuming it is, try and mount it:

```
sudo mkdir /mnt/mydrive
sudo mount /dev/sd**XY** /mnt/mydrive
```

X and Y are obviously disk and partition numbers.  If it mounted ok, look in /mnt/mydrive and check for your files; if it didn't mount, tell us what it said.

I tried```
sudo fdisk -l
```

And got:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23213b72

   Device Boot      Start         End      Blocks   Id  System

```

What now?.


I've never done anything like this before. Sorry.


Thanks.

---

### Post by JoeyF on 2010-04-26
> **mikewhatever said:**
> Linux live cds are not intended for recovering deleted data. If the data is intact and you just can't boot the system, it's a different story. For deleted files, testdisk is the tool.
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)



I tried your method but got no disc space remaining. Could I back up to a 4GB Flash Drive?.


Thanks.

---

### Post by Grenage on 2010-04-27
If the drive isn't showing partitions, then you'll probably want to use testdisk - so at what section of the guide does it run out of space?

---

### Post by iponeverything on 2010-04-27
I agree, grab testdisk. It looks like it just deleted your partition table. There is a good chance that all testdisk will need to do is recover the partition table and all the data will still be there.

I remember running some tests a while back.. I made a note of the partition table deleted it. I then went back and used fdisk to recreate the partition table exactly as it was.. and all the data was still there.

---

### Post by JoeyF on 2010-04-27
After I select Backup to Home and it scans for a second it tells me no space.


Is there anyway I can Backup certain files to my Flash Drive?. Or Reinstall Ubuntu and then recover the files to that?.


Thanks.

---

### Post by Grenage on 2010-04-28
Ahh.  You're running a LiveCD, which is running run entirely from the CD and RAM.  If you plug the USB drive in, you can probably restore files there.

That said, I have not used TD, so there is a chance it will simply restore all files, not giving you a nice list of files to choose from; the files may not even have names.  If that's the case, you'll need a storage medium that is at least equal to the volume of files you'll be restoring.

There are some good TD guides out there, all of which will be far more informative than me.

---

