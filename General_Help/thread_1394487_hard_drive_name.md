---
title: "hard drive name"
date: 2010-01-30
forum: General Help
---

### Post by david90 on 2010-01-30
What determines the device name of a hard drive?  I thought the port that the HD is plugged into determines it's name but that's not the case.  I have one HD in my ubuntu machine and it's /dev/sda regardless of which sata port I plug it into.

---

### Post by blueshiftoverwatch on 2010-01-30
> **david90 said:**
> What determines the device name of a hard drive?  I thought the port that the HD is plugged into determines it's name but that's not the case.  I have one HD in my ubuntu machine and it's /dev/sda regardless of which sata port I plug it into.
It's just what Linux names your different partitions. Your physical hard drive(s) doesn't have a name like that. But your partition(s) do. SDA is for SATA drives and HDA is for IDE drives.

---

### Post by M!K3_$ on 2010-01-30
edit: sorry, realized this has nothing to do with what you want. but i'll leave it here anyways



```
sudo fdisk -l
```

this will show you what hard drives you have and what partitions

for example

```

mike@ubuntu:~$ sudo fdisk -l
[sudo] password for mike: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x480a480a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdb: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders
Units = cylinders of 4420 * 512 = 2263040 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        3522     7778304    7  HPFS/NTFS

```


i have 2 drives (/dev/sda and /dev/sdb) sdb is actually an SD card.

you can see i have 2 partitions on my hard drive...

/dev/sda1 and /dev/sda2

---

### Post by M!K3_$ on 2010-01-30
> **blueshiftoverwatch said:**
> It's just what Linux names your different partitions. Your physical hard drive(s) doesn't have a name like that. But your partition(s) do. SDA is for SATA drives and HDA is for IDE drives.

So if you had another sata hard drive in your computer and you added a new sata drive to it, linux would call it /dev/sdb

/dev/sda just means that it's the first sata drive.

---

### Post by NightwishFan on 2010-01-30
hda is for the master ide drive, no matter where it is.

sda/b/c is for SATA/SCSI drives.

The number is for the partition on those drives.

---

### Post by david90 on 2010-01-30
> **NightwishFan said:**
> hda is for the master ide drive, no matter where it is.

sda/b/c is for SATA/SCSI drives.

The number is for the partition on those drives.

I guess my question is not clear. 

Is there a correlation between linux's hard drive names and the sata port that the hard drives are plugged into?  If I have one sata hard drive in my PC and I plug it into sata port #3, would linux call it /dev/sdc?

---

### Post by NightwishFan on 2010-01-30
It is the master drive found, so I would assume it would be sda. Any others, such as chipcard readers and USB would show up as sdb/c/d.

If another drive in slot 1 is master, putting another in slot3 would be sdb.

---

### Post by audiomick on 2010-01-30
> **david90 said:**
> I guess my question is not clear. 

Is there a correlation between linux's hard drive names and the sata port that the hard drives are plugged into?  If I have one sata hard drive in my PC and I plug it into sata port #3, [COLOR="Red"]would linux call it /dev/sdc?[/COLOR]

No.

I am not sure, in the case of a computer with _multiple_ drives, if there is a relationship between the sata port and the drive number.

Regardless of that, if the computer only has one drive, it is always sda. As has been pointed out, it used to be the case that a scsi drive was "sdx" and an IDE drive was "hdx". I think they are now all "sdx".

Be that as it may, the first drive is sda. Primary partitions are numbered 1 to 4. One of these can be an extended partition. The logical partitions therein always start at number 5, regardless of how many primaries there are.

The second drive is then sdb, the third sdc, and so on.

Here is the output of "fdisk" on my machine.
```
mick@ubuntu-desktop:~$ sudo fdisk -l
[sudo] password for mick: 

Platte /dev/sda: 80.0 GByte, 80026361856 Byte
255 Köpfe, 63 Sektoren/Spuren, 9729 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xc3f8aac4

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            3649        9729    48845632+   5  Erweiterte
/dev/sda3            1825        3648    14651280   83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux Swap / Solaris
/dev/sda6            3649        5593    15623149+  83  Linux
/dev/sda7            5594        9327    29993323+  83  Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x63eba0e6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1       60424   485355748+  83  Linux
/dev/sdb2           60425       60801     3028252+  82  Linux Swap / Solaris

```
sorry it is in German.;)

What you are seeing is:
on the first drive, sda
sda1 is the / of my main install.
sda3 is the / of an install that I made to test stuff
sda2 is an extended, which contains
sda5, a swap partition
sda6, the /home of the test install
sda7, a storage partition for archives

on the second drive, sdb
sdb1 is the /home of my main install
sdb2 is the second swap partition.

I have two swap partitions because my big fat smart book said that this can be faster than one big one, but I think it is not really such an advantage.

here is another example out of a thread here which I will not name of a drive that got out of hand.
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x639e8ffd

Partition  Boot         Start           End          Size  Id System

/dev/sda2          38,379,285   390,716,864   352,337,580   f W95 Ext d (LBA)
/dev/sda5          76,276,683   152,553,239    76,276,557  83 Linux
/dev/sda6         152,553,303   189,101,114    36,547,812  83 Linux
/dev/sda7         228,845,988   266,775,389    37,929,402  83 Linux
/dev/sda8         308,319,543   366,892,469    58,572,927   b W95 FAT32
/dev/sda9    *    189,101,178   227,094,839    37,993,662  83 Linux
/dev/sda10        227,094,903   228,845,924     1,751,022  82 Linux swap / Solaris
/dev/sda11         38,379,411    74,605,859    36,226,449  83 Linux
/dev/sda12         74,605,923    76,276,619     1,670,697  82 Linux swap / Solaris
/dev/sda13        266,775,453   306,504,134    39,728,682  83 Linux
/dev/sda14        306,504,198   308,319,479     1,815,282  82 Linux swap / Solaris
/dev/sda15        366,892,533   389,608,379    22,715,847  83 Linux
/dev/sda16        389,608,443   390,716,864     1,108,422  82 Linux swap / Solaris

```
in this case, sda2 is an extended partition. There are no primaries. All the other partitions are Logicals. This is not a problem on a Linux system, but having so many is not such a good idea without a good reason for it. 4 Swap partitions is the result of repeated installs, and not necessary.

---

### Post by louieb on 2010-01-30
> What determines the device name of a hard drive?boot order is the 1st factor - the 1st hdd in the boot order is sda, 2nd sdb ... 

Which sata port or ide channel only come into play when you have multiple hard drives. 

ie. say for example you have drives plugged into ports sata1 and sata3, and maybe an external drive pluged into a USB port.    

Any of the 3 could be sda depending on which you select to boot from. Thats why Ubuntu when to using a partitions UUID a couple of years ago. UUIDs don't usually change.

---

