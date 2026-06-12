---
title: "USB flash drive mounting problem"
date: 2010-09-08
forum: General Help
---

### Post by zarathustra@ on 2010-09-08
Hi all,
 

 x86-64 bit laptop. after inserting the USB key (flash drive), I see the icon of the mounted device, but **cannot access** it from the file browser. When I go to /media I see no USB flash drive mounted.  
 That's the log output at this point:
 

 XXX@Home-Desktop:~$ dmesg | tail 
 [15031.819575] sd 7:0:0:0: [sdb] Write Protect is off 
 [15031.819584] sd 7:0:0:0: [sdb] Mode Sense: 45 00 00 08 
 [15031.819589] sd 7:0:0:0: [sdb] Assuming drive cache: write through 
 [15031.820065] sr1: scsi3-mmc drive: 48x/48x tray 
 [15031.820267] sr 7:0:0:1: Attached scsi CD-ROM sr1 
 [15031.820404] sr 7:0:0:1: Attached scsi generic sg3 type 5 
 [15031.822694] sd 7:0:0:0: [sdb] Assuming drive cache: write through 
 [15031.822704]  sdb: sdb1 
 [15031.824941] sd 7:0:0:0: [sdb] Assuming drive cache: write through 
 [15031.824950] sd 7:0:0:0: [sdb] Attached SCSI removable disk 
 

 then I try to manually mount the device:
 

 XXX@Home-Desktop:~$ sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137 
 

 what happens at this point, is that the icon of the 16GB flash drive changes from USB **icon**, to a **“No Entry”** icon in Toolbar- Places, **BUT I can access it. **it's location now is in /media/external.

 

 Important info: a **day before**, when I first encountered this problem, there was the “no entry” icon in “Places” toolbar, and there was no access to the device. The only way I had access to it, was through “/media/34xyz”  (the flash drive light was blinking the whole time).
 

 I would appreciate your help solving this. Hope I gave you enough information.

---

