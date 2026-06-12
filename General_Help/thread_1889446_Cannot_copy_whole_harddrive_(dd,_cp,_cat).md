---
title: "Cannot copy whole harddrive (dd, cp, cat)"
date: 2011-12-01
forum: General Help
---

### Post by BurtaN on 2011-12-01
Hi,

I want to establish network booting on my laptop using gPXE and iSCSI. As installing Windows on the iSCSI target does not work for me, I've just created a fresh installation on my laptop and want to copy it into an image file (as described in the [etherboot wiki]("http://etherboot.org/wiki/sanboot/transfer")). However, I do not succeed in copying the MBR and the first partition, neither in copying the whole harddrive using the following commands.

```
dd if=/dev/sdX of=/path/to/image/file.img bs=8225280 count=1825 #MBR + first part
``````
dd if=/dev/sdX of=/path/to/image/file.img #whole drive
```I always get an input/output error.
Copying only the MBR
```

dd if=/dev/sdX of=/path/to/image/file.img bs=512 count=1 #MBR
```or copying the first partition is working fine.

```
dd if=/dev/sdX1 of=/path/to/image/file.img #first part
```Do you have any ideas? Thank you very much!
BurtaN

---

### Post by dandnsmith on 2011-12-01
Would you like to provide an *fdisk -l* listing of the HDD, so we can put the query in context?

In my experience it is very easy to have dd report i/o errors whereas they aren't significant.

Did you try the fdisk on the output file(s) as a check?

---

### Post by BurtaN on 2011-12-01
Yes of course:

```
root@fred-lap-ubuntu:~# fdisk -l /dev/sdb

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ad24e84

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *        2048   102604799    51301376    7  HPFS/NTFS/exFAT
```Exact dd command was following:

```

sudo dd if=/dev/sdb of=win7.img bs=512 count=102604799
dd: Lesen von „/dev/sdb“: Eingabe-/Ausgabefehler # input/outputerror
1576+0 Datensätze ein
1576+0 Datensätze aus
806912 Bytes (807 kB) kopiert, 31,1966 s, 25,9 kB/s

``````
sudo dd if=/dev/sdb1 of=win7.img
102602752+0 Datensätze ein
102602752+0 Datensätze aus
52532609024 Bytes (53 GB) kopiert, 587,077 s, 89,5 MB/s
```sudo dd if=/dev/sdb1 of=win7.img gives following

```
fdisk -l win7.img 

Disk win7.img: 52.5 GB, 52532609024 bytes
255 Köpfe, 63 Sektoren/Spur, 6386 Zylinder, zusammen 102602752 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

Das sieht nicht wie eine Partitionstabelle aus.
Sie haben wahrscheinlich das falsche Gerät ausgewählt.

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
win7.img1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
win7.img2   ?  1917848077  2462285169   272218546+  73  Unbekannt
win7.img3   ?  1818575915  2362751050   272087568   2b  Unbekannt
win7.img4   ?  2844524554  2844579527       27487   61  SpeedStor

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

---

### Post by dandnsmith on 2011-12-02
I can see a couple of things which cause me to doubt.
1. may be a difference of version of fdisk or disk hardware, in that the default reporting for fdisk -l seems to be in units of sectors rather than in cylinders (which has been a somewhat artifical concept for years now, with the advent of larger disks).
2. the count you have used, and the unit size for transfer for the whole-disk dd have resulted in only part of the disk being transferred - you'd have done better to use 'dd if=/dev/sdb of=...win7.img' to get the lot. The parameters used in the exemplar are intended to make the transfer more efficient, where your version has led to only part being transferred.

I'm confused as to how the last panel of results were obtained, as they seem to be listing multiple win7.imgx which haven't been hitherto mentioned.

I hope some of this comment helps you - by all means ask more if helps clarify things.

---

### Post by BurtaN on 2011-12-02
Ok, I have no shred the whole drive and now I can correctly dd it. I don't know what was wrong, but I think, it will work now...

Thank you anyway for your kind replies :)

---

