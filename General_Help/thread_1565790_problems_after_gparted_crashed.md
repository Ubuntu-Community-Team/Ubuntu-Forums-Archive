---
title: "problems after gparted crashed"
date: 2010-09-01
forum: General Help
---

### Post by jazzboarder on 2010-09-01
[SIZE=2]Hi guys.
I am pretty new to this forum (and ubuntu/linux in general) and am not sure if this is the right category.

A few days ago I wanted to resize my partition. I tried it with gparted. sadly, during the process it crashed and now I cannot boot this partition.
I got a second ubunto installed on a second partition of my hdd,
When I try to "check" said partition in gparted i get the following message:

>  [/SIZE][SIZE=2]GParted 0.5.1[/SIZE]
 [SIZE=2]Libparted 2.2[/SIZE]
    [SIZE=2]**Check and repair file system (ntfs) on /dev/sdb1**  00:00:00    ( ERROR ) [/SIZE]   [SIZE=2]    [/SIZE]    [SIZE=2] calibrate /dev/sdb1  00:00:00    ( SUCCESS ) [/SIZE]   [SIZE=2]    [/SIZE]     [SIZE=2][I]path: /dev/sdb1
start: 63
end: 775519824
size: 775519762 (369.80 GiB)[/I][/SIZE]         [SIZE=2] check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:00    ( ERROR ) [/SIZE]   [SIZE=2]    [/SIZE]     [SIZE=2]***ntfsresize -P -i -f -v /dev/sdb1***[/SIZE]    [SIZE=2]    [/SIZE]     [SIZE=2][I]ntfsresize v2.0.0 (libntfs 10:0:0)
$MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
ERROR(5): Opening '/dev/sdb1' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.[/I][/SIZE][SIZE=2] 


I tried working with ntfsfix but after i run "sudo ntfsfix /dev/sdb1" I get the following message.

[/SIZE]> Mounting volume... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... $MFT has invalid magic.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.[SIZE=2]

I am grateful for any suggestions.
[/SIZE]

---

### Post by oldfred on 2010-09-01
As it says you need to run chkdsk from windows repair CD.

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by jazzboarder on 2010-09-01
> **oldfred said:**
> As it says you need to run chkdsk from windows repair CD.

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

thx,
I tried running chkdsk, but it only checked the partition on which win7 is running.  :(

I guess I'll try testdisk again then

---

### Post by oldfred on 2010-09-01
If you do not specify chkdsk runs in the boot partition. If you have more than one NTFS partition you have to specify D: or whatever letter it sees it as.

---

### Post by jazzboarder on 2010-09-01
> **oldfred said:**
> If you do not specify chkdsk runs in the boot partition. If you have more than one NTFS partition you have to specify D: or whatever letter it sees it as.

yeah i thought so. the problem is that it doesn't list the partition at all.
it only lists c:
(testdisk and gparted (for example) show the "broken/missing" partition though.

---

### Post by jazzboarder on 2010-09-02
I tried TestDisk, but I have no clue what the program is telling me or how it could help me with my program

maybe somebody has some advice?

---

### Post by oldfred on 2010-09-02
I have not used testdisk. But if the heads are 240 and it says change to 255 I would try that. All systems now use 255.



Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by jazzboarder on 2010-09-25
pushing this a bit, maybe somebody else has some advice?

---

