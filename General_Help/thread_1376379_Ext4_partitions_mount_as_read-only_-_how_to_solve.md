---
title: "Ext4 partitions mount as read-only - how to solve?"
date: 2010-01-09
forum: General Help
---

### Post by aryangor on 2010-01-09
Hey, all!

I have 4 partitions. One is Ext4 for Karmic, one is NTFS for WinXP, and the other two are Ext4 where I keep all my stuff.

When I boot into Karmic and open Nautilus, none of the last three are auto mounted. When I click on one of them, instead of a window popping out asking me for a sudo password, I get a message as shown below.

[IMG]http://i306.photobucket.com/albums/nn278/aryangor/mount-error.jpg[/IMG]

If I try to mount via sudo in terminal it works, but the files for me are then all read-only. Again, if I open Nautilus as root, all works fine.

What I want is the following:
- for all 3 partitions to automount on startup;
- for all 3 partitions to be owned by me and not by root.

I tried editing /etc/fstab, but to no avail. Neither did running "chown" help.

Any help is appreciated.

_/etc/fstab:_
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=13eac906-c8bc-4283-9726-3c5ae9544351 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0238a1c5-827c-47ee-b5a5-2aa3ff669523 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Windows (ntfs)
/dev/sda5       /media/winxp    auto    users,auto,sync,rw,umask=000 0 0
# Stuff (ext4)
/dev/sda6       /media/stuff    auto    users,auto,sync,rw,umask=000 0 0
# Stuff2 (ext4)
/dev/sda7       /media/stuff2   auto    users,auto,sync,rw,umask=000 0 0
# VirtuaBox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

---

### Post by ibuclaw on 2010-01-09
My initial instinct would be to run fsck on the file systems.

Ensure they are unmounted
```

sudo umount /dev/sda6
sudo umount /dev/sda7

```
Then run fsck
```

sudo fsck -fyv /dev/sda6
sudo fsck -fyv /dev/sda7

```
Regards
Iain

---

### Post by aryangor on 2010-01-09
> **tinivole said:**
> My initial instinct would be to run fsck on the file systems.

Ensure they are unmounted
```

sudo umount /dev/sda6
sudo umount /dev/sda7

```
Then run fsck
```

sudo fsck -fyv /dev/sda6
sudo fsck -fyv /dev/sda7

```
Regards
Iain
>>>>>>>>>>>>>>>>>>>

Unmounted both, fsck'ed both - same error message in Nautilus. :(

>>>>>>>>>>>>>>>>>>>
sudo fsck -fyv /dev/sda6
fsck from util-linux-ng 2.16            
e2fsck 1.41.9 (22-Aug-2009)             
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure      
Pass 3: Checking directory connectivity   
Pass 4: Checking reference counts         
Pass 5: Checking group summary information

      42 inodes used (0.00%)
       5 non-contiguous files (11.9%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 31/1                
 1666293 blocks used (5.78%)                         
       0 bad blocks                                  
       2 large files                                 

      27 regular files
       6 directories  
       0 character device files
       0 block device files    
       0 fifos                 
       0 links                 
       0 symbolic links (0 fast symbolic links)
       0 sockets                               
--------                                       
      33 files                                 
>>>>>>>>>>>>>>>>>>>>>>>>>>>>
sudo fsck -fyv /dev/sda7
fsck from util-linux-ng 2.16            
e2fsck 1.41.9 (22-Aug-2009)             
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure      
Pass 3: Checking directory connectivity   
/lost+found not found.  Create? yes       

Pass 4: Checking reference counts
Pass 5: Checking group summary information

stuff2: ***** FILE SYSTEM WAS MODIFIED *****

   75324 inodes used (0.88%)
    3171 non-contiguous files (4.2%)
       2 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 75026/283/5
30533711 blocks used (89.44%)
       0 bad blocks
       7 large files

   67237 regular files
    8077 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
>>>>>>>>>>>>>>>>>>>

---

### Post by ibuclaw on 2010-01-09
OK, can you post the output of
```
dmesg | tail -30
```
then.

That will give a better hint as to what may be happening, as we have ruled out (mostly) corrupted file system.

Regards
Iain

---

### Post by aryangor on 2010-01-09
> **tinivole said:**
> OK, can you post the output of
```
dmesg | tail -30
```
then.

That will give a better hint as to what may be happening, as we have ruled out (mostly) corrupted file system.

Regards
Iain

dmesg | tail -30

[   51.938897] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   51.938905] end_request: I/O error, dev sr0, sector 483944           
[   51.938912] Buffer I/O error on device sr0, logical block 120986     
[   53.011128] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   53.011136] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]          
[   53.011143] Info fld=0x1d89a, ILI                                            
[   53.011146] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   53.011155] end_request: I/O error, dev sr0, sector 483944
[   53.011161] Buffer I/O error on device sr0, logical block 120986
[   53.964266] UDF-fs: No VRS found
[   53.964272] UDF-fs: No partition found (1)
[   54.024026] ISO 9660 Extensions: Microsoft Joliet Level 3
[   54.024553] ISOFS: changing to secondary root
[   54.104145] EXT4-fs (sda6): Unrecognized mount option "umask=000" or missing value
[   54.461220] EXT4-fs (sda7): Unrecognized mount option "umask=000" or missing value
[   54.557793] EXT4-fs (sda6): Unrecognized mount option "umask=000" or missing value
[   54.709971] EXT4-fs (sda7): Unrecognized mount option "umask=000" or missing value
[   57.477636] ACPI: EC: GPE storm detected, transactions will use polling mode
[   57.977063] ACPI: EC: missing confirmations, switch off interrupt mode.
[   61.465385] EXT4-fs (sda7): Unrecognized mount option "umask=000" or missing value
[   69.422006] EXT4-fs (sda7): barriers enabled
[   69.438195] kjournald2 starting: pid 2876, dev sda7:8, commit interval 5 seconds
[   69.438614] EXT4-fs (sda7): internal journal on sda7:8
[   69.438619] EXT4-fs (sda7): delayed allocation enabled
[   69.438624] EXT4-fs: file extents enabled
[   69.438927] EXT4-fs: mballoc enabled
[   69.438945] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   69.738402] EXT4-fs (sda6): Unrecognized mount option "umask=000" or missing value
[   69.783930] EXT4-fs (sda6): Unrecognized mount option "umask=000" or missing value
[  173.328038] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x013f0c00

Seems to me there is a serious complaint about "umask=000" ??

---

### Post by aryangor on 2010-01-09
oops sorry for the double post :)

---

### Post by ibuclaw on 2010-01-09
> **aryangor said:**
> dmesg | tail -30

[   54.024553] ISOFS: changing to secondary root
[   54.104145] EXT4-fs (sda6): Unrecognized mount option "umask=000" or missing value
[   54.461220] EXT4-fs (sda7): Unrecognized mount option "umask=000" or missing value
[   54.557793] EXT4-fs (sda6): Unrecognized mount option "umask=000" or missing value
[   54.709971] EXT4-fs (sda7): Unrecognized mount option "umask=000" or missing value

Seems to me there is a serious complaint about "umask=000" ??

Ohh! I see that now.
Ext4 does not support the **umask** option. That is only for FAT and NTFS filesystems
```
sudo sed -i '/sda6\|sda7/{s/,umask=000//}' /etc/fstab
```
Will remove those errant lines.

Regards
Iain

---

### Post by aryangor on 2010-01-09
> **tinivole said:**
> Ohh! I see that now.
Ext4 does not support the **umask** option. That is only for FAT and NTFS filesystems
```
sudo sed -i '/sda6\|sda7/{s/,umask=000//}' /etc/fstab
```
Will remove those errant lines.

Regards
Iain

Did as u said. After rebooting the partitions were auto mounted exactly as I wanted! I then ran

```
sudo chown -Rv myusername /media/stuff && sudo chown -Rv myusername /media/stuff2
```

and it did the read-write trick.

Thanks, Iain, you are priceless - so stay safe in the rough UK weather ok? :)

---

### Post by ibuclaw on 2010-01-09
> **aryangor said:**
> 
Thanks, Iain, you are priceless - so stay safe in the rough UK weather ok? :)
Thanks, and no probs. Weather is doing fine (infact - it's just started snowing again).

Since your problem has rectified, I'll mark this thread as solved.

Regards
Iain

---

