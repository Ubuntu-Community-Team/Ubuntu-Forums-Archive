---
title: "system wipe"
date: 2011-04-16
forum: General Help
---

### Post by geogur on 2011-04-16
how do i wipe the system runing ubuntu 10.04? can i use sudo fdisk tryed many times but cant find the right command .

---

### Post by yetiman64 on 2011-04-16
> **geogur said:**
> how do i wipe the system runing ubuntu 10.04? can i use sudo fdisk tryed many times but cant find the right command .

From a live cd use

```
sudo fdisk -l
``` (-l, small letter L) to see your partitions and their appropriate device numbering (eg. /dev/sda1, /dev/sdb2 etc) alternatively you could use gparted from System > Administration > Gparted to do the same task graphically.

 BE VERY CAREFUL WITH THE NEXT COMMAND.

On finding the correct partitions to erase, for each partition  issue the command in terminal,

```
sudo shred --force --iterations=0 --verbose --zero /dev/sdXY
``` in /dev/sdXY, X is the drive letter and Y is the partition number you checked for earlier.

On completing the wipe in terminal open gparted (mentioned earlier), here you can choose to reformat the partition easily (this will be needed if you erase a partition).

If you do an erase on a complete drive (by not including the partition number with the above command) then you will have to also set a new partition table to the drive. This can be done with gparted as well, using the Device menu > Create partition table. You then set an ms-dos type partition table here.

Once again take care with shred (or dd if you use it,) it can be devastating if used incorrectly. Using dd recently cost me ~75 GB of data, thank goodness I had reasonable backups to refer to.

---

### Post by geogur on 2011-04-16
thanx want to wipe all giving old clunker away and want all data gone .

---

### Post by yetiman64 on 2011-04-16
> **geogur said:**
> thanx want to wipe all giving old clunker away and want all data gone .

If you need secure erasure and not just for reinstalling change iterations=0 to iterations=3 (or delete the switch altogether as 3 passes is default for shred). This will take a bit longer obviously, but is far more secure if giving a machine away.

---

### Post by geogur on 2011-04-16
okay well on my way used sudo fdisk -l have my list thanx again

---

### Post by seawolf167 on 2011-04-16
Alternatively, you can also use *dd*

```
dd if=/dev/zero of=/dev/sda bs=1M
```where you replace /dev/sda with your to-be-wiped drive

Note that this command will take quite a while to complete and it writes 0's to all sectors

---

### Post by dragonfly41 on 2011-04-17
This app apparently wipes _any_ disks it can see .. so it needs careful usage.  I haven't used it myself.

[http://sourceforge.net/projects/dban/](http://sourceforge.net/projects/dban/)

Also I bookmarked this from a recent thread.   See references to forensics.

[http://www.deer-run.com/~hal/](http://www.deer-run.com/~hal/)

---

### Post by oklokl on 2011-04-17
[http://www.jetico.com/wiping-bcwipe/](http://www.jetico.com/wiping-bcwipe/)
BCWipe-1.9-8.tar.gz
./configure
make
make install

[COLOR=Red]&#65279;bcwipe[/COLOR][COLOR=Red] -F /media/test[/COLOR]
[COLOR=#FF0000](wipe free space on mounted filesystem[/COLOR])



bcwipe version 1.9-8 rev 319 2010-10-04  Copyright 1994-2010 Jetico, Inc.
Usage: bcwipe [OPTIONS]... FILE...
Remove FILE(s) with wiping.
OPTIONS:
  -mb       German BCI/VISTR 7-pass wiping
  -md       U.S. DoD 5220-22M 7-pass extended character rotation wiping
  -me       U.S. DoE 3-pass wiping
  -mf<file> read wiping scheme from file. See *notes below
  -mg       (default) 35-pass wiping by Peter Gutmann
  -ms       7-pass wiping by Bruce Schneier
  -mt       1-pass test mode: fill the start of 512-byte block with block number
  -mz       1-pass zero wiping
  -m N      U.S. DoD 5220-22M N-pass extended character rotation wiping

  -w        disable verification
  -n sec    NAS mode: wait sec seconds between wiping passes. See **notes below
  -s        use ISAAC random instead of SHA-1
 [COLOR=#FF0000] -p        use random pattern instead of full random[/COLOR]
  -r        process the contents directories recursively
  -f        force wiping, never prompt        (use with caution)
  -d        do not delete file(s) after wiping
  -b        wipe contents of block devices    (use with caution)
   -B        disable direct IO access mode for block devices  -t N       use N threads to wipe block devices. Useful for multiple disk devices.   -S        wipe file slacks
[COLOR=#FF0000]  -F        wipe free space on mounted filesystem[/COLOR]
  -i        prompt before any removal (y/[n]/a)
              y - yes, n - no(default), a - yes for all
  -I        disable interactive prompt
  -v        verbose modebcwipe: invalid option -- '-'

---

