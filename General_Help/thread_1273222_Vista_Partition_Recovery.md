---
title: "Vista Partition Recovery"
date: 2009-09-23
forum: General Help
---

### Post by razor07 on 2009-09-23
-I have a Dual boot, Ubuntu 9.04 and Vista. I defragmented my Vista, after a restart it said BOOTMGR missing. 

-I couldnt mount that partition even in Ubuntu. On Inserting the vista recovery CD it failed to detect any vista OS on the hard-disk and the alternative mentioned was, if nothing detected...load the drivers for the hard-disk. 

-Using my Dell driver CD i tried installing a few SATA drivers(As I was unsure of the exact driver name) but it didnt work. 

-The thing that happend after few trials is, in Ubuntu if I mount that partition it only shows a Temp folder and two files in it(I guess those formed due to use of Dell Utilities check),rest is empty.

-Is there a way to get it back to normal ?
Otherwise even if I get my data back I'am happy :) ! so is there some tool that can go through that partition and get my files along with their names...

---

### Post by tommcd on 2009-09-23
It sounds like your Vista installation might be hosed. You can try using a System Rescue CD to recover any data that may be left on your Vista partition:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer](http://www.sysresccd.org/Sysresccd-manual-en_Backup_data_from_an_unbootable_windows_computer)
Good luck. Post back about what system rescue CD has found.

And welcome to the Ubuntu forums!

---

### Post by oldfred on 2009-09-23
You probably should first try to repair you Vista partition.
Seee the last to this page for repairing Vista boot:
[http://talsemgeest.doesntexist.com/2009/09/19/bootloader-how-to/](http://talsemgeest.doesntexist.com/2009/09/19/bootloader-how-to/)

If your PC did not come with a complete Vista installation CD, you can download a Vista Recovery Disc at the following link:
Windows Vista Recovery Disc [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

If all that fails then you can use testdisk on tommcd's recommended Systemrescue CD or if you can boot Ubuntu you can download it from Synaptic.

---

