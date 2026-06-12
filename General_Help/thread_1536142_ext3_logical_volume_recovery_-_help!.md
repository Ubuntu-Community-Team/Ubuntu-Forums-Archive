---
title: "ext3 logical volume recovery - help!"
date: 2010-07-21
forum: General Help
---

### Post by carolinason on 2010-07-21
anyone know of tool that will recover files from an ext3 logical volume, i am assuming there is a damaged partition table. but i am not sure. 10 years linux, but no recovery experience.  

the drive had three partitions two primaries at either end and an extended in the middle. in the extended where two logical partitions, one ext4 and one ext3. the ext3 is where the data that NEEDS to be recovered is.

the system is a dual boot - sata drives hooked to simple adaptec card - wouldn't you know it windows xp was used to format a previous ntfs  the first primary on the drive and this yorked it. windows xp will see the partitions, but gparted only sees non allocated space on the entire drive - not even the ntfs - disk internals found the files, but the first run crapped out after 8 hours. am trying the boot cd - i was wondering if there was a tool that is on system rescue cd - i see sfdisk, but it appears it saves a partition table???

any help would be insanely appreciated.

thanks

-never i mean, never use windows to create even its own partitions.

---

### Post by hansdown on 2010-07-21
Hi carolinason.

Boot into a live ubuntu cd.

Open a terminal, and enter,

```
gksudo nautilus
```

This will give you the necessary permissions, to drag and drop your files to a usb.

---

### Post by carolinason on 2010-07-21
okay give me a sec

---

### Post by carolinason on 2010-07-21
okay i am in a 10.04 live cd session and i have launched nautilus - looking around too

---

### Post by jerome1232 on 2010-07-21
If it's just the partition table that's wonky then testdisk may be of great use.


You can install it to a live cd from a terminal like this (yes you can install software to a live cd without touching the disk, it just stores it in system ram or in swap so long as you have enough of those it works)

```
sudo apt-get install testdisk
```

Then run testdisk on the disk, it will try and detect the partition tables, I'm sure you can find some great test disk tuts if you Google it a bit.


If you wanted to run testdisk on the first drive in your system, it won't make any immediate changes to disk but make sure you are carefully reading what it's telling you. If you unsure about anything your doing ask here before committing to a change, provide as much info as possible (such as a screenshot of testdisk for example)

```
sudo testdisk /dev/sda
```


Testdisk also comes with photorec which is a great tool for recovering destroyed data if it comes down to that.

---

### Post by carolinason on 2010-07-21
can't find testdisk for some reason did a search and nothing and looked for tes and disk and didn't see anything either - however i ran sfdisk -l and got this 

```
  Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+   6416    6417-  51544521    7  HPFS/NTFS
/dev/sdb2       6417+  60539   54123- 434742463    5  Extended
/dev/sdb3      60540   60800     261    2096482+  82  Linux swap / Solaris
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5       6441+ 174334- 167893- 1348599808    0  Empty
		start: (c,h,s) expected (1023,254,63) found (0,0,0)
		end: (c,h,s) expected (1023,254,63) found (0,0,0)
/dev/sdb6      12912+  60539   47628- 382571878+  83  Linux

```

---

### Post by carolinason on 2010-07-21
sdb5 is where the files are

---

### Post by jerome1232 on 2010-07-21
try running sudo apt-get update first, then sudo apt-get install testdisk.

Pretty sure it's in the universe repositories so make sure those are enabled. Def looks like a partition issue to me.

---

### Post by carolinason on 2010-07-21
enabled other software repos waiting - looking for testdisk

---

### Post by carolinason on 2010-07-21
sorry - testdisk is installed

i'll run the program - /* edit */

---

### Post by carolinason on 2010-07-21
sorry for all the chatter, but i'm in testdisk and this program is really cool! but i'm in a little over my head though.

here is the first curses screen 

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0   1  1  6416 254 63  103089042 [New Volume]
 2 E extended              6417  16 62 60539 254 63  869484926
 3 P Linux Swap           60540   0  1 60800 254 63    4192965
No partition is bootable
   X extended             273766 105  5 273790 162 36     389183
Must be in extended partition
 2 E extended              6417  16 62 60539 254 63  869484926
   X extended             273766 105  5 273790 162 36     389183


```

i'm looking for a logical and it has L for logical i select continue and it asks if the partition was created in vista, it was created in xp so i said N and i get 

```
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  6416 254 63  103089042 [New Volume]
L Linux                 6417   1  1 12911 254 63  104342112
L Linux                12912   1  1 60539 254 63  765143757
P Linux Swap           60540   0  1 60800 254 63    4192965

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue



```

uuuhhh

---

### Post by carolinason on 2010-07-21
your the man! i'm going to try and copy some files. i read that i could back up the entire drive, but have to step literally across the street and pick up a 1TB drive. this drive is 500GB the files are that valuable. 

thanks!

---

### Post by jerome1232 on 2010-07-21
Let it be noted I'm not partition expert just a computer hobbyist. So take everything I say with a grain of salt.

Okay I'm trying to analyze everything and

From testdisks initial output you have some funky stuff going on.

Testdisks last output is it's fixed version. Seems to have just corrected the start and end points of your logical partitions.

It's corrected layout makes sense to me and looks good if you look at the numbers, seems to just have corrected where the partitions started and ended. Doing a backup before preceding is a very wise plan. I would image your entire drive to the 1 tb disk, you can use ping, clonezilla, or dd to do that. (dd comes installed with ubuntu, clonezilla and ping are more advanced imaging programs than dd).

Good luck.

---

### Post by carolinason on 2010-07-22
everything worked out great. i didn't back up the entire drive (my piggy bank was dry so i couldn't get a larger drive). i simply copied the files to another partition and then chose [write] in testdisk to write out the corrected part table. the table isn't perfect as you see here

```
Disk /dev/sdb: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        6417    51544521    7  HPFS/NTFS
/dev/sdb2            6418       60540   434734965    f  Extended LBA
/dev/sdb5           12913       60540   382563877   83  Linux
Warning: Partition 5 does not end on cylinder boundary.
/dev/sdb3           60541       60801     2088450   82  Linux swap

```

but i can work with it until i get everything back in line. testdisk is obviously a powerful and helpful tool.

thanks jerome1232

---

