---
title: "Partition is misaligned by 3071 bytes"
date: 2011-11-16
forum: General Help
---

### Post by Boker939 on 2011-11-16
Hi, 


Ive installed a new 2TB Western Digital harddrive into my Ubuntu 11.10 machine, I used the Disk Utility to format it in NTFS and mount with the label TV1, I did not partition this disk, just left is as a single 2tb volume after formatting. This harddrive was working great for a long time aswell, then recently I needed to turn off my machine for awhile, and when I turned it back on a few days later, I wasn't able to access the hard drive anymore... the label name is now listed twice in the Devices column on the left hand side when I open a file explorer window, when I move the mouse over either the tool tip which appears is "Mount and open TV1", I get the error message 

"Error mounting: Mount exited with exit code 12 NTFS signature is missing. Failed to mount '/dev/sda1':Invalid argument
The device '/dev/sda1': doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a partition (e.q. /dev/sda, not /dev/sda1)? or the other way around?"

(I was using this harddrive as a storage location of a .VHD file which was created using VirtualBox however I didn't experience any problems with this)

When looking at the harddrive using the Harddrive Utility, the harddrive is now partitioned very strangely, into 4 chunks, two labeled as TV1 and 2 listed as unallocated space.

And the two paritions which have the label TV1 show the below error message:
"Warning: the partition is misaligned by 3072 bytes" and the other TV1 labeled volume says something similar with 2048 bytes.

Is there a way I can correct this and keep the content on this hard drive?

Thanks

---

### Post by oldfred on 2011-11-17
NTFS partitions have to have a NTFS signature in the partition boot sector at the beginning of each NTFS partition. If bootable it then also has the boot flag and reference to whichever version of Windows it is booting.

If partition table was corrupted testdisk may be able to restore it. It often finds the old partition table info and lets you choose which partition(s) to restore. But you have to have a good idea of partition layout to know what to recover.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

If NTFS signature is also missing, it may be able to restore it, but try to restore partitions first.
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

