---
title: "mdadm error replacing a failed disk"
date: 2011-10-21
forum: General Help
---

### Post by Saline2 on 2011-10-21
[FONT="Arial"]Hi Helpful Ubuntu Folks,

  I have a four disk mdadm RAID5 on which one of the disk failed. The disk just completely died and was not visible by the OS. I powered down, took the disk out, restarted and left the array unstarted. I then bought a new disk and I'm now trying to add to the array and get the array back on its feet.

Here is what the "detail" command tells me:
[/FONT]
[FONT="Courier New"]excession# mdadm -D /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Sun May 29 18:32:22 2011
     Raid Level : raid5
  Used Dev Size : 1465137152 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Oct 21 22:26:06 2011
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : excession:0  (local to host excession)
           UUID : 557a3ef8:14251ba9:d4aa50ac:bd9b7d5c
         Events : 136609

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       0        0        2      removed
       4       8       48        3      active sync   /dev/sdd

[/FONT]
[FONT="Arial"]My new disk has been detected by the OS and assigned to /dev/sdc, which was the same designation as the old failed disk. When I try to add the new disk I get a really unhelpful error message:[/FONT]

[FONT="Courier New"]excession# mdadm --manage /dev/md127 --add /dev/sdc
mdadm: add new device failed for /dev/sdc as 5: Invalid argument

[/FONT][FONT="Arial"]and when I try to run the arary, I get an equally unhelpful message:[/FONT]

[FONT="Courier New"]excession# mdadm --run /dev/md127              
mdadm: failed to run array /dev/md127: Input/output error

[/FONT]
[FONT="Arial"]
Can someone please help me understand what mdadm is doing and how to get my array back?

Thanks,
Saline
[/FONT]

---

### Post by RED666 on 2012-12-05
Hi Saline,
I read somewhere you solved this! Can you give me a hand?
[http://ubuntuforums.org/showthread.php?t=2089826&page=2](http://ubuntuforums.org/showthread.php?t=2089826&page=2)

---

