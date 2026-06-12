---
title: "Cannot change permissions"
date: 2010-04-03
forum: General Help
---

### Post by sn0m on 2010-04-03
HI chaps
sth happened and I cannot sync my nokia 5800 in memory card mode with my laptop.
It says sth that certain files or folders are read only.
Tried to change permissions but no luck.
Can someone have a look and tell me what I'm doing wrong.
this is it:
koli@koli-laptop:~$ n
sending incremental file list

sent 7412 bytes  received 21 bytes  14866.00 bytes/sec
total size is 11073190  speedup is 1489.73
sending incremental file list
Dystonia.doc
ECG.doc
Hyponatremia.doc
Pediatrics.doc
PreEclampsiaandEclampsia.doc
Pregnacy.doc
RSI.doc
SIRS.doc
Thoraccotomy in emergency department.doc
ThrombolysingMi.doc
child_sick.doc
Pictures/coagulation cascade.jpg
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Dystonia.doc.kVrbEb" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.ECG.doc.cLyLoA" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Hyponatremia.doc.q3Qn9Y" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Pediatrics.doc.qMG4Tn" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.PreEclampsiaandEclampsia.doc.eABNEM" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Pregnacy.doc.u0uApb" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.RSI.doc.AMFpaA" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.SIRS.doc.6AEjVY" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Thoraccotomy in emergency department.doc.WhrfGn" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.ThrombolysingMi.doc.ac2crM" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.child_sick.doc.uTdgcb" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/Pictures/.coagulation cascade.jpg.gbAmXz" failed: Read-only file system (30)

sent 193219 bytes  received 249 bytes  386936.00 bytes/sec
total size is 11820356  speedup is 61.10
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]
building file list ... 
10 files to consider
./
rsync: failed to set times on "/media/MemoryCard/mp3_radio_files/.": Read-only file system (30)
Faktori.wmv.mp3
       6.05M 100%   58.55MB/s    0:00:00 (xfer#1, to-check=8/10)
Faktori03-April.mp3
      10.03M 100%   35.31MB/s    0:00:00 (xfer#2, to-check=7/10)
chillout.03-April.mp3
      56.22M 100%   46.58MB/s    0:00:01 (xfer#3, to-check=6/10)
comedy.02-April.mp3
      56.64M 100%   49.06MB/s    0:00:01 (xfer#4, to-check=5/10)
discolancio.02-April.mp3
      54.19M 100%   57.17MB/s    0:00:00 (xfer#5, to-check=4/10)
nkpt.03-April.mp3
      47.23M 100%   27.05MB/s    0:00:01 (xfer#6, to-check=3/10)
paradiserock.02-April.mp3
      55.82M 100%   34.62MB/s    0:00:01 (xfer#7, to-check=2/10)
proshqip.02-April.mp3
      44.32M 100%   34.50MB/s    0:00:01 (xfer#8, to-check=1/10)
summerdance.02-April.mp3
      42.63M 100%   46.46MB/s    0:00:00 (xfer#9, to-check=0/10)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.Faktori.wmv.mp3.pqyM0f" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.Faktori03-April.mp3.LVSxZG" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.chillout.03-April.mp3.xQPOh8" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.comedy.02-April.mp3.fQp3aB" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.discolancio.02-April.mp3.rL25M5" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.nkpt.03-April.mp3.j70eRB" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.paradiserock.02-April.mp3.Twg4i9" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.proshqip.02-April.mp3.Jpx4kI" failed: Read-only file system (30)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.summerdance.02-April.mp3.9u0mCi" failed: Read-only file system (30)

sent 373.18M bytes  received 186 bytes  57.41M bytes/sec
total size is 373.14M  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]
building file list ... 
3 files to consider
./
rsync: failed to set times on "/media/MemoryCard/Videos/video_zone/.": Read-only file system (30)
rsync: delete_file: unlink(_PAlbTN/topfest30mars2010.flv.mp4_128x96) failed: Read-only file system (30)
rsync: delete_file: unlink(_PAlbTN/2XL.wmv.mp4_128x96) failed: Read-only file system (30)
cannot delete non-empty directory: _PAlbTN
faktori03-April.mp4
     134.62M 100%   59.42MB/s    0:00:02 (xfer#1, to-check=0/3)
rsync: mkstemp "/media/MemoryCard/Videos/video_zone/.faktori03-April.mp4.YzA50j" failed: Read-only file system (30)

sent 134.64M bytes  received 34 bytes  53.85M bytes/sec
total size is 685.96M  speedup is 5.09
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]
koli@koli-laptop:~$ cd /media/MemoryCard/
koli@koli-laptop:/media/MemoryCard$ chmod -R a+w *.* mp3_radio_files/
chmod: changing permissions of `356910035451210.ndif': Read-only file system
chmod: changing permissions of `card_content.cid': Read-only file system
chmod: changing permissions of `card_content.xml': Read-only file system
chmod: changing permissions of `CRITOE.doc': Read-only file system
chmod: changing permissions of `DevIcon.fil': Read-only file system
chmod: changing permissions of `DevLogo.fil': Read-only file system
chmod: changing permissions of `route.dat': Read-only file system
chmod: changing permissions of `routeHeader.dat': Read-only file system
chmod: changing permissions of `settings.dat': Read-only file system
chmod: changing permissions of `Untitled 1.doc': Read-only file system
chmod: changing permissions of `WMPInfo.xml': Read-only file system
chmod: changing permissions of `workout.dat': Read-only file system
chmod: changing permissions of `workoutHeader.dat': Read-only file system
chmod: changing permissions of `mp3_radio_files/': Read-only file system
koli@koli-laptop:/media/MemoryCard$ sudo chmod -R a+w *.* mp3_radio_files/
[sudo] password for koli: 
chmod: changing permissions of `356910035451210.ndif': Read-only file system
chmod: changing permissions of `card_content.cid': Read-only file system
chmod: changing permissions of `card_content.xml': Read-only file system
chmod: changing permissions of `CRITOE.doc': Read-only file system
chmod: changing permissions of `DevIcon.fil': Read-only file system
chmod: changing permissions of `DevLogo.fil': Read-only file system
chmod: changing permissions of `route.dat': Read-only file system
chmod: changing permissions of `routeHeader.dat': Read-only file system
chmod: changing permissions of `settings.dat': Read-only file system
chmod: changing permissions of `Untitled 1.doc': Read-only file system
chmod: changing permissions of `WMPInfo.xml': Read-only file system
chmod: changing permissions of `workout.dat': Read-only file system
chmod: changing permissions of `workoutHeader.dat': Read-only file system
chmod: changing permissions of `mp3_radio_files/': Read-only file system
koli@koli-laptop:/media/MemoryCard$ 

thanks in advance
Sokol

---

### Post by ibuclaw on 2010-04-03
You've mounted it as a read-only filesystem.

umount and remount again with '-o rw'

(edit): just what filesystem does your device use by the way?

---

### Post by Martje_001 on 2010-04-03
This filesystem is mounted as read-only. You cannot write to it, unless you mount it as read-write.

Edit: Should've refreshed this page. ibuclaw beat me.

---

### Post by sn0m on 2010-04-03
Well I haven't mount it on read only, the mount media manager of ubuntu mounts it automatically.
Is there a way of changing it cas it's doing sth wrong...
ta
Sokol

---

### Post by Martje_001 on 2010-04-03
What's the output of:
```
sudo fdisk -l
```

---

### Post by sn0m on 2010-04-03
koli@koli-laptop:~$ sudo fdisk -l
[sudo] password for koli: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa226c290

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         973     7815591   82  Linux swap / Solaris
/dev/sda2   *         974        4161    25607040+   7  HPFS/NTFS
/dev/sda3            4162        5680    12201367+  83  Linux
/dev/sda4            5681       19457   110663752+  83  Linux

Disk /dev/sdc: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders
Units = cylinders of 4420 * 512 = 2263040 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        3522     7778304    b  W95 FAT32
koli@koli-laptop:~$

---

### Post by Martje_001 on 2010-04-03
Unmount your disk and in a terminal do:
```
sudo mkdir -p /media/disk
sudo mount /dev/sdc1 /media/disk
```
Does it give you any errors?

---

### Post by sn0m on 2010-04-03
well kind off..##

koli@koli-laptop:~$ sudo mkdir -p /media/disk
[sudo] password for koli: 
koli@koli-laptop:~$ sudo mount /dev/sdc1 /media/disk
koli@koli-laptop:~$ n
sending incremental file list

sent 7433 bytes  received 21 bytes  2981.60 bytes/sec
total size is 10922200  speedup is 1465.28
sending incremental file list
Amylase.doc
COPD.doc
CVP.doc
CspineRules.doc
DislocatedHip.doc
Dystonia.doc
ECG.doc
Hyponatremia.doc
Pediatrics.doc
PreEclampsiaandEclampsia.doc
Pregnacy.doc
RSI.doc
SIRS.doc
Thoraccotomy in emergency department.doc
ThrombolysingMi.doc
child_sick.doc
Pictures/coagulation cascade.jpg
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Amylase.doc.GDuMBm" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.COPD.doc.pmTnBw" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.CVP.doc.8CE1AG" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.CspineRules.doc.9fCSAQ" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.DislocatedHip.doc.c8YLA0" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Dystonia.doc.xqwNAa" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.ECG.doc.GUiRAk" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Hyponatremia.doc.j9FXAu" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Pediatrics.doc.ikwDBE" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.PreEclampsiaandEclampsia.doc.9b1lCO" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Pregnacy.doc.qdMbDY" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.RSI.doc.jyY3D8" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.SIRS.doc.E2m5Ei" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.Thoraccotomy in emergency department.doc.zc98Fs" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.ThrombolysingMi.doc.GU3eHC" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/.child_sick.doc.LQCsIM" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/MedicalNotes/Pictures/.coagulation cascade.jpg.uvaLJW" failed: Permission denied (13)

sent 248349 bytes  received 345 bytes  165796.00 bytes/sec
total size is 12079474  speedup is 48.57
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]
building file list ... 
12 files to consider
./
rsync: failed to set times on "/media/MemoryCard/mp3_radio_files/.": Operation not permitted (1)
Faktori.wmv.mp3
       6.05M 100%   47.82MB/s    0:00:00 (xfer#1, to-check=10/12)
Faktori03-April.mp3
      10.03M 100%   33.34MB/s    0:00:00 (xfer#2, to-check=9/12)
HeavyMetal.03-April.mp3
      58.36M 100%   41.54MB/s    0:00:01 (xfer#3, to-check=8/12)
chillout.03-April.mp3
      56.22M 100%   10.61MB/s    0:00:05 (xfer#4, to-check=7/12)
comedy.02-April.mp3
      56.64M 100%    8.89MB/s    0:00:06 (xfer#5, to-check=6/12)
comedy.03-April.mp3
      55.28M 100%   14.85MB/s    0:00:03 (xfer#6, to-check=5/12)
discolancio.02-April.mp3
      54.19M 100%   27.14MB/s    0:00:01 (xfer#7, to-check=4/12)
nkpt.03-April.mp3
      47.23M 100%   24.95MB/s    0:00:01 (xfer#8, to-check=3/12)
paradiserock.02-April.mp3
      55.82M 100%   29.14MB/s    0:00:01 (xfer#9, to-check=2/12)
proshqip.02-April.mp3
      44.32M 100%   27.29MB/s    0:00:01 (xfer#10, to-check=1/12)
summerdance.02-April.mp3
      42.63M 100%   33.02MB/s    0:00:01 (xfer#11, to-check=0/12)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.Faktori.wmv.mp3.pNkCCB" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.Faktori03-April.mp3.WqppTU" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.HeavyMetal.03-April.mp3.twLVse" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.chillout.03-April.mp3.CdgYWz" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.comedy.02-April.mp3.DSIG13" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.comedy.03-April.mp3.ahzpzH" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.discolancio.02-April.mp3.lsHH6p" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.nkpt.03-April.mp3.QKvoob" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.paradiserock.02-April.mp3.BdQnjY" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.proshqip.02-April.mp3.eDp95M" failed: Permission denied (13)
rsync: mkstemp "/media/MemoryCard/mp3_radio_files/.summerdance.02-April.mp3.ngBWbD" failed: Permission denied (13)

sent 486.84M bytes  received 224 bytes  24.97M bytes/sec
total size is 486.78M  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]
building file list ... 
3 files to consider
./
rsync: failed to set times on "/media/MemoryCard/Videos/video_zone/.": Operation not permitted (1)
rsync: delete_file: unlink(_PAlbTN/topfest30mars2010.flv.mp4_128x96) failed: Permission denied (13)
rsync: delete_file: unlink(_PAlbTN/2XL.wmv.mp4_128x96) failed: Permission denied (13)
cannot delete non-empty directory: _PAlbTN
faktori03-April.mp4
     134.62M 100%   56.49MB/s    0:00:02 (xfer#1, to-check=0/3)
rsync: mkstemp "/media/MemoryCard/Videos/video_zone/.faktori03-April.mp4.ymGbsg" failed: Permission denied (13)

sent 134.64M bytes  received 34 bytes  53.85M bytes/sec
total size is 685.96M  speedup is 5.09
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]
koli@koli-laptop:~$

---

### Post by Martje_001 on 2010-04-03
And:
```
sudo touch /media/disk/Test
```
?

(After mounting it, of course)

---

### Post by sn0m on 2010-04-03
well kaboom
I had enough, so decided to re-install ubuntu.
Now I have a separate home directory, /home and has been fine in the past when re-istalling ubuntu.
Well this time.
Some st...d encrypt something has created some crazy encrypt thing in my old home directory and there is no way I can access it.
I can mount it and thats it, when accessing koli, which is my old home directory, is all empty, nada in there. However when doing right click I says that the drive is 41% free. But the files are not accessible.
What on earth....I'm so anoyed right now, being locked out of your files when deadlines and stuff are looming, is not so nice.
I'm sorry but right now I'm having a bad moment, kind off why should I put up with all thissss...

---

