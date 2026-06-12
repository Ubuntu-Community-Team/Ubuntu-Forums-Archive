---
title: "Cannot mount my usb"
date: 2011-11-06
forum: General Help
---

### Post by baxy77bax on 2011-11-06
Ok so what i did is i wanted to boot (install) a new ubuntu version on my laptop. so i downloaded the iso and everything and placed that on my stick(laptop does not have cd-drive).

After finishing i removed the stick and tried to transfer some data using that stick. but now it seams that  no os recognizes my stick any more in the sence that i cannot mount the stick on any computer. 

dmesg | tail 
[440516.185847] scsi 35:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[440516.187731] sd 35:0:0:0: Attached scsi generic sg6 type 0
[440516.376670] sd 35:0:0:0: [sdf] 16121856 512-byte logical blocks: (8.25 GB/7.68 GiB)
[440516.377419] sd 35:0:0:0: [sdf] Write Protect is off
[440516.377424] sd 35:0:0:0: [sdf] Mode Sense: 23 00 00 00
[440516.377428] sd 35:0:0:0: [sdf] Assuming drive cache: write through
[440516.380229] sd 35:0:0:0: [sdf] Assuming drive cache: write through
[440516.380235]  sdf:
[440516.382500] sd 35:0:0:0: [sdf] Assuming drive cache: write through
[440516.382508] sd 35:0:0:0: [sdf] Attached SCSI removable disk

and after mounting i get the following message


dmesg | tail 
[440516.376670] sd 35:0:0:0: [sdf] 16121856 512-byte logical blocks: (8.25 GB/7.68 GiB)
[440516.377419] sd 35:0:0:0: [sdf] Write Protect is off
[440516.377424] sd 35:0:0:0: [sdf] Mode Sense: 23 00 00 00
[440516.377428] sd 35:0:0:0: [sdf] Assuming drive cache: write through
[440516.380229] sd 35:0:0:0: [sdf] Assuming drive cache: write through
[440516.380235]  sdf:
[440516.382500] sd 35:0:0:0: [sdf] Assuming drive cache: write through
[440516.382508] sd 35:0:0:0: [sdf] Attached SCSI removable disk
[440871.943395] FAT: bogus number of reserved sectors
[440871.943402] VFS: Can't find a valid FAT filesystem on dev sdf.


What to do now, How to fix this?

baxy

---

### Post by Kyoushuu on 2011-11-06
Does your USB show up in Disk Utility? Try removing the partition if it is (will delete all contents of drive).

---

### Post by baxy77bax on 2011-11-06
Thnx now it is working :)

---

