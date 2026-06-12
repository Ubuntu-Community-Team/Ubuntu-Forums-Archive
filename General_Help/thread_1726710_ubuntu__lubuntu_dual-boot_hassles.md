---
title: "ubuntu / lubuntu dual-boot hassles"
date: 2011-04-11
forum: General Help
---

### Post by flemur13013 on 2011-04-11
Hi All and Happy Monday!

I've got a dual-boot ubuntu & lubuntu system set up, and it was a real PITA to get going as the installer consistently screws things up: after the lubuntu install I have to go in afterwards to fix things by hand (editing grub files, etc) to make both OSs visible and bootable.  (FWIW, I think the installers are pretty poor and grub2 is truly AWFUL, and they scare away a lot of people who might switch from MS to Linux - see the "Ubuntu replaced Windows" thread!).

So I'd like to accomplish two things:

(1) Have a stable ubuntu install on the first partition (primary, sda1) and install/uninstall/screwup/fiddlewith other Linux distros on the 2nd partition (primary, sda3) without killing the ubuntu on sda1, and without fighting with grub2 each time.

(2) Find out about and fix the "sector 67378240" error mentioned below.  I think it's left over from when the lubuntu install pointed the default boot to sda3 rather than sda1, which I (might have) "fixed" with update-grub (plus file editing, since grub never automatically sees both bootable OSs).

 +++

The installer presents this choice:
(a) Install alongside existing, or 
(b) Choose partitions

Since I already have an ext4 partitition for the 2nd OS, I want to "Install Alongside" AND "Choose the partition"

- which one to select?

(a) Automatically chooses the wrong install partition (it wants to make a new one).
(b) Makes Ubuntu not show on the boot menu w/o post-install fiddling.


Right now everything's running properly - so it seems - but running the "boot info script" (bootinfoscript.sourceforge.net) gives me the below, note the error about sda1:

++++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++ START Boot Info Script output +++++++++++++++++

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 67378240 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   
(NOTE: I mount this as /home in both distros, and also use it for mp3s, etc).
sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
(NOTE: This is a *copy* of a Win 7 install - I don't think it's bootable and don't want to boot it. I use this NTFS  partition with VirtualBox and an XP guest).

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

(lubuntu installed on sda3)
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   102,398,309   102,396,262  83 Linux
/dev/sda2         195,313,662 1,465,144,064 1,269,830,403   5 Extended
/dev/sda5         195,313,664   199,311,359     3,997,696  82 Linux swap / Solaris
/dev/sda6         199,318,518   711,486,719   512,168,202  83 Linux
/dev/sda7         711,486,783 1,465,144,064   753,657,282   7 HPFS/NTFS
/dev/sda3         102,400,000   195,311,615    92,911,616  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        065a27b8-85c3-424e-8cfc-542039b968f5   ext4       ubuntu                        
/dev/sda2: PTTYPE="dos" 
/dev/sda3        da203b75-005e-41ff-a526-f800c87d9873   ext4       lubuntu                       
/dev/sda5        1083ed9d-1e8e-4d4a-be90-b3aaaae868c5   swap                                     
/dev/sda6        e389c61b-4609-4e3a-bf24-ad600ef209ed   ext4       home                          
/dev/sda7        2B2A35E0415336EF                       ntfs       ntfs                          
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /mnt/NTFS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /home                    ext4       (rw)

....truncated for space ...

++++++++++++++++++++++++++++++++++++++++++++++++++++++
++++++++ EOF Boot Info Script info +++++++++++++++++++


TIA for any help or ideas! (I hope this made a little bit of sense....)

---

