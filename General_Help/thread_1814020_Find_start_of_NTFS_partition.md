---
title: "Find start of NTFS partition?"
date: 2011-07-28
forum: General Help
---

### Post by stands2reason on 2011-07-28
Hello. I have an NTFS partition which is no longer being recognized by anything as a valid file system. I've noticed that its start is larger than the end of the previous partition by a few thousand sectors (and the previous one doesn't end on a cylinder boundary).

Is there a way I can search for the start of the partition and mount that location, and is there a way I can change the size/start of the partition without deleting it?

---

### Post by Joris Donders on 2011-07-28
Well, for starters your Windows should recognize that partition. No doubt. 

But for Ubuntu, that is just the difference; it can write on that partition but it doesn't see it.

What to do? 

You can boot with a LiveCD and start up Gparted; then you can make that partition to Linux standards (ext3 e.g.) 

It depends a little of what you want to do.

---

### Post by stands2reason on 2011-07-28
This is a partition that was shrunk (but *supposedly* not moved using GParted). It is not recognized as a valid file system, but I don't know if this has something to do with the start of the partition being incorrect. 

Is there a way I can search through, say, a DD image of my hard drive for the start of an NTFS partition and then mount that location?

---

### Post by jerrrys on 2011-07-28
overlapping partitions is not good.  some people say its best to use a windows partition manager for NTFS, but i have not had a problem using gparted.  the only time this is a bad idea is with windows vista; gparted and windows vista will not play nice and will probably bork vista.  and gparted will not allow you to overlap partitions.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId335513](http://www.dedoimedo.com/computers/gparted.html#mozTocId335513)

---

### Post by oldfred on 2011-07-29
You need to be careful as which partition does the part that is overlapping belong to? Hopefully no data has been written by either partition into the overlapping area.

First backup existing partition table:
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS

---

### Post by staticd on 2011-07-29
Can you post the output of ```
sudo fdisk -l /dev/sda
```Download testdisk. In my experience it was awsomely useful in recovering deleted/ corrupted partions. you can just download the tar ball and run it from a live CD.


```
cp /media/Mypendrive/testdisk-6.11.3 ~/testdisk-6.11.3
sudo testdisk-6.11.3/linux/testdisk_static

```

---

### Post by stands2reason on 2011-07-29
> **staticd said:**
> Can you post the output of ```
sudo fdisk -l /dev/sda
```


Sure:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              14        9455    75842865    7  HPFS/NTFS
/dev/sda3           10955       12162     9691136   83  Linux


```

Partition 2 is the one I'm having trouble with.Partition 1 is the 100MB System Reserved which has the Windows boot loader. GRUB is still working and it loads the Windows boot loader, but the Windows loader apparently can't recognize the parition either.

I have installed and tried using testdisk, but I can't get it to display any of the contents of sda2.

---

### Post by oldfred on 2011-07-29
This may give more detail:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

