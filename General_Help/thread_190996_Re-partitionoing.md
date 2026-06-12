---
title: "Re-partitionoing"
date: 2006-06-06
forum: General Help
---

### Post by shade11 on 2006-06-06
I have this other ccomputer of mine that is dual booting with Ubuntu and Windows XP. I would like to be able to remove the Ubnuntu partition and merge it with the Windows NFTS partition. But I do not know how. 

It is not my primary PC mind you, but I dont want to damage the hard drive. There is too much stuff to backup on the computer so i dont want to re-format the entire HDD.

---

### Post by aysiu on 2006-06-06
I don't know about merging, but from Windows you can certainly reformat the partition to be NTFS or FAT32.

I think it's the Control Panel--Administrative Tools > Computer Management > Disk Management. Something like that.

---

### Post by shade11 on 2006-06-07
So this tool can delete partitions then add the deleted partition to the NFTS drive? But isn't is dangerous to edit partitions from the hard drive?

---

### Post by aysiu on 2006-06-07
[QUOTE=shade11]So this tool can delete partitions then add the deleted partition to the NFTS drive? But isn't is dangerous to edit partitions from the hard drive?[/QUOTE] Not as long as they're partitions that are different from the one you're using.

---

### Post by Fred Doolie on 2006-06-07
Winblows can certainly reformat your ubuntu partitionbut can not merge it into the other one. After you reformat boot up a DOS floppy with fdisk on it and enter "fdisk /MBR" to restore a standard Master Boot Record and get rid of Grub.

The way to do what you want without losing data is to use Partition Magic.  PM can do wonderful things to partitons and not lose the data. 

WARNING WARNING WARNING WARNING WARNING
Partition Magic is also called Partition TRAGIC! Sometimes it gets confused and farkles up everything making all yoiur partitions garbage. In that case you have to reformat everything and start over clean. The best way to use PM is to think to yourself "PM is my first and laziest choice but I don't mind losing everything on my drives if I have to".

---

### Post by Fred Doolie on 2006-06-07
Duplicate post. How did THAT happen?

---

### Post by shade11 on 2006-06-08
Is there something else I can use other than PM?

---

### Post by Fred Doolie on 2006-06-08
A few others but they are all $$$$$.  So is PM but it's a proven application.
Unless you want to reparttion and reformat (losing everything on the drive) there's no other (free) way to merge the partitions. Windoze sure sucks up your $$$ doesn't it?

Why not just use the other partition as a data storage? That way if (I mean when) you reinstall Winslows some day the stuff in there won't be lost?

What wrong with Ubuntu?  You never said. Personally I think it's loads better than Winpoop and I'm only keeping my system dual boot for the games.

-------------
Do you have a large external drive? Why not do a system backup to it, repartition/format/install Win again and then restore the backup over it?
*** Not tested but should work ***

---

### Post by giants_fan on 2006-06-08
[QUOTE=shade11]Is there something else I can use other than PM?[/QUOTE]
You should be able to use the QtParted.  You can get it from [here]("http://www.sysresccd.org/Main_Page").

You would 1) download the iso 2) burn it 3) reboot your computer 4) delete the ubuntu (ext3?) partition and 4) resize your nt (ntfs) partition.  

Basically, QtParted is a free Partion Magic clone.  Unlike PM, however, you boot from it (as opposed to running from within windows ala PM).

---

### Post by Fred Doolie on 2006-06-08
> Basically, QtParted is a free Partion Magic clone.

It is? Linux wins again!

---

### Post by shade11 on 2006-06-08
I dont want to mess up my partitions, what is one of the good paid ones.

---

### Post by aysiu on 2006-06-08
The best program I've found it DiskDrake. It comes standard on a PCLinuxOS live CD, and it's free.

---

### Post by denjin on 2006-06-08
If you feel like spending money guarantees you won't have a problem, then Partition Magic is good.

Otherwise, the latest Knoppix CD has a recent version of QTParted on it, which works great.  I don't recommend using the gparted that comes with Ubuntu as it is fairly old (unless they have backported all the changes from .3 to the .1 that Ubuntu uses).

---

### Post by shade11 on 2006-06-09
Does DiskDrake do NFTS? And is Partition Magic from Symantec?

---

### Post by aysiu on 2006-06-09
DiskDrake does NTFS, but then so does GParted and QTParted.

The thing I like about DiskDrake is that it doesn't freeze up on me or gray out valid options. It lets you do what you want to do.

And, unlike Partition Magic, DiskDrake is free.

---

### Post by bryanlking on 2006-06-09
[QUOTE=shade11]I dont want to mess up my partitions, what is one of the good paid ones.[/QUOTE]

I can understand your not wanting to mess up your computer but PLEASE, don't waste your money on a paid for solution.  You don't need to.  It's a waste, waste, waste.

Free software solutions are just fine.  Very straight-forward, easy, and dependable.  I've formatted, repartioned, etc. countless times using the free tool in Kanotix.

Free software is all you really need.

BK

---

### Post by bryanlking on 2006-06-09
Sorry, forgot to say the tool from Kanotix..

Qtparted!

Works like a champ.

BK

---

### Post by shade11 on 2006-06-09
I am going to try out DiskDrake.

So disk drake is able to get these partitions merged right? What would I do? Do i delete the Ubuntu partition and then enlarge the Winblows partition. I have to be sure.

---

