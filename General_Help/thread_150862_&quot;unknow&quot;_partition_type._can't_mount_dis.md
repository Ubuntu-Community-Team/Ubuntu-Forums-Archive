---
title: "&quot;unknow&quot; partition type. can't mount disk"
date: 2006-03-26
forum: General Help
---

### Post by General Moskovich on 2006-03-26
I had a perfectectly working system until I tried to install winxp on a second HD. I don't think I did anything to disk 1 (breezy's install).

I've used a live cd run qtparted and get the following layout:

[PHP]
Disks
|---/UNIONFS/dev/hda         <--- Breezy
|---/UNIONFS/dev/hdb         <--- Windows
|---/UNIONFS/dev/hdc         <--- DVD


Number        Partition           Type         Status     Size                    
|-- 01        /UNIONFS/dev/hda1   ext3         Active     243.14MB
|-- 02        /UNIONFS/dev/hda2   extended                37.03GB
    |-- 03    /UNIONFS/dev/hda5   unknow                  37.03GB

Used space    Start       End           Label
26.95MB       0.03MB      247.17MB      /boot
N/A           247.17MB    37.27GB
N/A           247.17MB    37.27GB
[/PHP]

hda2 is all NTFS. So obviously I messed up and wiped my swap partition. Is there anyway I can recover the data on hda5? 

Thanks!

Mosko

---

