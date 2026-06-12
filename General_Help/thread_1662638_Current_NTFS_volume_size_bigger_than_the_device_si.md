---
title: "Current NTFS volume size bigger than the device size!"
date: 2011-01-08
forum: General Help
---

### Post by neu5eeCh on 2011-01-08
Well... I've made a mess of things. I tried using GParted to resize an NTFS partition (not mission critical but I'd rather repair than reformat). I'm presently writing from PartedMagic. I've done some searching on this error message and it seems to be solvable. If any of you have solved this issue yourself and can give it to me straight and simple, I would appreciate it. In the meantime, I'll begin searching. (I'm not confident enough to be sure that solutions given elsewhere will apply to my situation - command lines might need to be tweaked?]

> Check and repair file system (ntfs) on /dev/sda5  00:00:01    ( ERROR )
        
calibrate /dev/sda5  00:00:01    ( SUCCESS )
        
path: /dev/sda5
start: 178000263
end: 597612934
size: 419612672 (200.09 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )
        
ntfsresize -P -i -f -v /dev/sda5
        
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda5
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 224731066880 bytes (224732 MB)
Current device size: 214841688064 bytes (214842 MB)
ERROR: Current NTFS volume size is bigger than the device size!
Corrupt partition table or incorrect device partitioning?[B]

Edit: [/B]I used TestDisk (available on PartedMagic CD) to rewrite the MBR. I would write the exact steps except that I don't remember them precisely. If you run into this problem, Google ["Current NTFS volume size bigger than the device size!" Testdisk]

---

