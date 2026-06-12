---
title: "Mounting Windows FakeRaid"
date: 2010-10-30
forum: General Help
---

### Post by MIsterBox on 2010-10-30
[FONT=UbuntuBeta] My friends,
I  know this is a common topic among the Ubuntu questions, and I assure  you I have tried every relevant thread extensively, but nothing I have  found seems to have worked. I have two Hitachi 1TB hard drives on a  FakeRaid 0 run under an Intel P55 chip that contains a Windows 7  installation and storage partitions. On a completely separate,  non-raided hard drive, I have this Ubuntu installation. I'm trying to  bridge the gap between the to OS's by mounting the second partition of  the FakeRaid 0. Here's what I know:
 - Disk Utility shows both Windows hard drives separated and lists them under /dev/sda1 and /dev/sdb1.
- If I run dmraid -ay, this is the output:
    ```
 ERROR: sil: only 3/4 metadata areas found on /dev/sdc, electing...
    /dev/sdb: "isw" and "ddf1" formats discovered (using ddf1)!
    /dev/sda: "isw" and "ddf1" formats discovered (using ddf1)!
    ERROR: sil: wrong # of devices in RAID set "sil_afbgdeafceca" [1/0] on /dev/sdc
    ERROR: removing inconsistent RAID set "sil_afbgdeafceca"
    RAID set "ddf1_New_VD" was activated
```[/FONT][FONT=UbuntuBeta] -dmraid -r outputs:
     ```
ERROR: sil: only 3/4 metadata areas found on /dev/sdc, electing...
    /dev/sdb: "isw" and "ddf1" formats discovered (using ddf1)!
    /dev/sda: "isw" and "ddf1" formats discovered (using ddf1)!
    /dev/sdc: sil, "sil_afbgdeafceca", linear, ok, 625140910 sectors, data@ 0
    /dev/sdb: ddf1, ".ddf1_disks", GROUP, ok, 1953394096 sectors, data@ 0
    /dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 1953394096 sectors, data@ 0
```[/FONT][FONT=UbuntuBeta] -Once  dmraid -ay is run, Disk Utility then shows the 2TB raid under  'Peripheral Devices', but it is clear that the device is not mounted in  any way.
-Finally, attempting to mount with 'sudo mount -t ntfs-3g /dev/mapper/ddf1_New_VD /media/storage' outputs:
     ```
NTFS signature is missing.
    Failed to mount '/dev/mapper/ddf1_New_VD': Invalid argument
    The device '/dev/mapper/ddf1_New_VD' doesn't seem to have a valid NTFS.
    Maybe the wrong device is used? Or the whole disk instead of a
    partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```[/FONT][FONT=UbuntuBeta] -I'm running Lucid 10.04 with the kernal 2.6.32-25-generic
 And this is all that I have tried. Any thoughts? Please let me know if  more information is needed, and I'd be happy to provide it. Thank you  for any and all help in advance.
[/FONT]

---

### Post by Eddison on 2010-10-30
Sorry I don't have any suggestions for RAID question, except one suggestion- GET RID OF WINDOWS!!  but you probably need it for something :(

Eddison

---

### Post by ronparent on 2010-10-31
Prior answer may not be at all useful -hope I can do better.

What level or raid is it? Dmraid apparently doesn't support all levels supported by windows. This doesn't appear to be the problem because it seems to be a two disk set?

Would Ubuntu be on sdc. In that case you may have to erase persistent meta data left over from the disk's prior usage as a raid. This may be interfering with the proper handling of the raid set. But, one problem at a time.

The saving grace may be that dmraids primary purpose is in discovering raid and that unless you tried partitioning operations on a raid nothing would be disrupted.

---

### Post by MIsterBox on 2010-11-03
> **ronparent said:**
> Prior answer may not be at all useful -hope I can do better.

What level or raid is it? Dmraid apparently doesn't support all levels supported by windows. This doesn't appear to be the problem because it seems to be a two disk set?

Would Ubuntu be on sdc. In that case you may have to erase persistent meta data left over from the disk's prior usage as a raid. This may be interfering with the proper handling of the raid set. But, one problem at a time.

The saving grace may be that dmraids primary purpose is in discovering raid and that unless you tried partitioning operations on a raid nothing would be disrupted.

Sorry for the delay. I thought I was subscribed to this thread, but clearly I am not. It's a Raid0, and yes, Ubuntu is on it's on drive under 'sdc'. The problem I'm getting hung on is that dmraid seems to activate it, but I'm not sure what I'm doing wrong in terms of actually mounting it.

Thanks for the help.

---

