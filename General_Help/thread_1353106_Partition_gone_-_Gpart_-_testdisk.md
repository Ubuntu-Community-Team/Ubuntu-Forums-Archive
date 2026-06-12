---
title: "Partition gone - Gpart - testdisk"
date: 2009-12-12
forum: General Help
---

### Post by humbfig on 2009-12-12
Hi

I was trying to upgrade 8.10 to 9.04 when I got this:


[IMG]http://dl.dropbox.com/u/2881715/GParted.jpg[/IMG]

sda1 is a windows partition, sda5 a linux swap, sda3 a EXT3 partition and sda6 used to be my Ubuntu partition.
The PC does not boot anymore (GRUB error 17). I installed Ubuntu 9.10 from scratch on another disk and that is how I run GParted, or on a live CD.

I would like your help to recover my lost partition (sda6). I do not care about this entire disk since I could use the free space on my PC to put a larger one. I can backup both the windows partition and the EXT3 (sda3) partition since I can mount it.
So, I would like to be able to either repair the disk (not absolutely necessary) or at least to recover the files that must still be in sda6 partition. Must be there because as far as I know I did not do any harm to the partition.......

I have been experimenting with "Gpart" but it seems it never ends looking for partitions....
Also with "parted", but I have no idea what to write on "rescue START END". Is start and end a sector number? a cylinder number? Anyway, I'd like to backup the files before entering such command.
Also with testdisk, which outputs:

[IMG]http://dl.dropbox.com/u/2881715/testdisk.jpg[/IMG]


thanks for your help

HumbFig

---

### Post by humbfig on 2009-12-12
Been digging a bit with testdisk. It says "partition can not be recovered". 
Starting to worry....... should I?
Anyone?

HumbFig

---

### Post by humbfig on 2009-12-15
> **humbfig said:**
> Been digging a bit with testdisk. It says "partition can not be recovered". 
Starting to worry....... should I?
Anyone?

HumbFig


well, this site is as useless as ubuntu......
I can't recover the partition with testdisk. I tried photorec. Great, all files are there, I can backup to another disk. 
But I have no space left on the other disk. It's ok, I connect a USB disk with lots of free space. I will free some space on the internal disk by copying files to the USB disk.
Oh, 2 MB/s speed to transfer the files...... the usual..... it's ok, I can navigate the web for 2 hours while the files are transfered....... Oh, wait, there's no internet browser in ubuntu, I mean, there are a lot, but none can deal with flash....... it's ok, I will play a game while the files are transfered....... I like LBreakOut2...... Oh, wait, the video board can't deal with such a modest game, must be the proprietary driver I installed (NVidea). I will roll back to the ubuntu driver..... Oh, I can't install the ubuntu driver, an error comes up, WTF, I will watch TV while the files are beeing copied.
2 hours later: Nice, finished copying. Now let me erase the files I copied. Done. Now let's empty the trash...... strange, there are no files in the trash...... and there's no free space on the drive. I erase files but the space doesn't free up...... this is a new one!!!!!! 
Let's make sure. I copy a 1GB file to the disk. I erase it. I have 1 GB less on the disk. Brilliant!!!!!!!!!! 
Today I will install windows (after 5 years windows free!) to free up space on the drive. I actually miss the blue screen.........

HumbFig

---

