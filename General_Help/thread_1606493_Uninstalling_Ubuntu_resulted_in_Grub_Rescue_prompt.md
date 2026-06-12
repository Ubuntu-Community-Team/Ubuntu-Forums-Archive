---
title: "Uninstalling Ubuntu resulted in Grub Rescue prompt"
date: 2010-10-26
forum: General Help
---

### Post by Jayblah on 2010-10-26
[COLOR=Black]Hello all,

I have two hard-drives. The first, C:\ (sda1) has Windows 7 x64  installed on it. The second hard-drive, D:\ (sdb1), was partitioned when  I installed Ubuntu 10.04 into two separate partitions: NTFS and Ext3.[/COLOR] [COLOR=Black]

I wanted to remove the Ext3/Ubuntu partition and reclaim that space  (i.e. completely remove Ubuntu). I did NOT install using Wubi. I booted  up Win7 x64, went into Disk Management, right-clicked the D:\ partition  corresponding to the Ext3 filesystem (shows up as unrecognized in Disk  Management), and opted to delete the volume. I then right-clicked on the  NTFS D:\ partition, and opted to Extend the Volume to reclaim the  previously partitioned space.[/COLOR] [COLOR=Black]

When I rebooted, I ended up with the following error:[/COLOR] [COLOR=Black]
```
error: no such device: f81368be-ea53-43d2-b8de-bb52b5ac322c.
grub  rescue>
```[/COLOR][COLOR=#888888][COLOR=Black]

I cannot get beyond this screen. Rebooting always puts me at the grub rescue prompt. I have looked at the *HOWTO: Purge* and *Grub Rescue Prompt* threads, but was not able to understand the instructions and am therefore asking for your help. However, I *was* able to install the boot script as those threads suggest, and here is my results.txt:

[/COLOR][/COLOR]```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,465,127,999 1,465,127,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,465,143,286 1,465,141,239   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1CFE4B73FE4B43EC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        04F08A92F08A8A1E                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/04F08A92F08A8A1E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/1CFE4B73FE4B43EC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


```I don't wish to retain Ubuntu. I simply want my partitioned drive back to NTFS and the ability to boot into Windows 7. Any assistance would be greatly appreciated. 

Thank you.

---

### Post by Quackers on 2010-10-26
Grub was your bootloader. When you got rid of Ubuntu it did not clear Grub. Grub is written to the MBR of your disc. You will need to repair your Windows installation by using the repair disc and fixing the MBR

---

### Post by Jayblah on 2010-10-26
> **Quackers said:**
> Grub was your bootloader. When you got rid of Ubuntu it did not clear Grub. Grub is written to the MBR of your disc. You will need to repair your Windows installation by using the repair disc and fixing the MBR

When I attempt to boot from CD/DVD using my Windows installation disc, I get the same error as before:

```
[COLOR=Black]error: no such device: f81368be-ea53-43d2-b8de-bb52b5ac322c.
grub  rescue>[/COLOR]
```[COLOR=Black]

I can, however, boot into the Live CD of Ubuntu 10.04 (which is how I made the initial post).
[/COLOR]

---

### Post by wojox on 2010-10-26
Since your already on a Live CD try [How to fix your Windows MBR with an Ubuntu liveCD]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

---

### Post by Quackers on 2010-10-26
That doesn't sound good. Either there is a problem with the Windows disc, or it isn't bootable. There are sites that offer downloads for Windows repair discs, I would go googling for one.
There is a method for putting the .iso on to a usb and making it bootable, which may be another option for you.
Alternatively lilo may be an option too.

---

### Post by dondiego2 on 2010-10-26
[SIZE=2]I also have a two drive installation[/SIZE] [SIZE=2]but I want ubuntu!

Anyway, I got that grub rescue prompt when I was struggling upgrading from 10.01 to 10.10.  I thought everything was running good and I got that prompt on startup.  I ended up going into my BIOS and changing the boot order of my drives and that cured it.  

I don't know if this helps with your problem but that's how I got mine fixed.[/SIZE]

---

### Post by Jayblah on 2010-10-26
I was able to fix my MBR by using Lilo. I tried to find ms-sys using Wojox' link, but it wasn't available. In case anyone else has similar issues, I was able to do it as follows:

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Rebooted and Windows 7 loaded as normal. Thank you for your time and effort in helping me resolve the issue, all.

---

