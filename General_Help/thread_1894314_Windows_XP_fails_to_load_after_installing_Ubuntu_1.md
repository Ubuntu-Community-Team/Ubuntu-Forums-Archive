---
title: "Windows XP fails to load after installing Ubuntu 11.10"
date: 2011-12-12
forum: General Help
---

### Post by kez1304 on 2011-12-12
Hi guys,

I'm new to the Linux scene, but have run into a problem already.

I installed Ubuntu 11.10 on my PC, which already had Windows XP on it. I did so with an Ubuntu live USB stick. Tried it out for a couple of days, then decided to install it. So I let it create a new partition for Ubuntu, then let it install.

Now however, when I'm greeted with the GRUB menu, if I select the Windows XP option, I see the 'Windows was not shutdown properly...' menu, with the 'Safe Mode', 'Safe Mode (with networking)', 'Safe Mode (with command line)', 'Start Windows normally', 'Last known good settings', etc. options.

Whichever one I pick, the screen just goes black, and the computer restarts.

Ubuntu works fine, which is what I'm using at the moment, but I do really need to get access to Windows again. I can navigate to the Windows partition fine, and access all the files, I just can't boot into windows itself.

I've heard that I might be able to use Super Grub Disk or Rescatux to fix this problem... But I don't want to risk doing any serious damage to the computer or my data. Can anyone advise on how to get Windows working again?

Here's my boot info script info:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.3 GB, 82347195904 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160834367 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   112,066,364   112,066,302   7 NTFS / exFAT / HPFS
/dev/sda2         112,066,558   160,833,535    48,766,978   5 Extended
/dev/sda5         112,066,560   156,710,911    44,644,352  83 Linux
/dev/sda6         156,712,960   160,833,535     4,120,576  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        EC4491024490D0A6                       ntfs       
/dev/sda5        5fa62776-1c2d-467f-9449-25f58fd5e44c   ext4       
/dev/sda6        9a590607-4e23-45c3-8c5c-c1fe293c3128   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

```

---

### Post by Frogs Hair on 2011-12-12
Have a look at this thread . [http://ubuntuforums.org/showthread.php?t=1891495&highlight=update+grub](http://ubuntuforums.org/showthread.php?t=1891495&highlight=update+grub)

---

