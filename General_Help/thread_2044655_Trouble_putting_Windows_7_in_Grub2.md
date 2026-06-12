---
title: "Trouble putting Windows 7 in Grub2"
date: 2012-08-19
forum: General Help
---

### Post by Fezze on 2012-08-19
Hi all, this is my first post on the Ubuntu Forms, and I am hoping I could get some support with successfully booting my windows 7 partition from grub2 based on my set up. I have tried super grub disk and have searched for documentation, but to no avail. 

Originally I was trying to to a net install of Ubuntu, to delete my old Vista partition that was 100+gb and in my way, and to have a Linux system to boot. I had also installed Windows 7 beside Vista and had decided I liked Windows 7 more. 

Unfortunately the net install, which was booted off of a usb drive (/dev/sda/) refused to install grub to the main hard disk (/dev/sdb/) even when directed to for some odd reason, and the Lilo install would crash also. And that follows the partitioner so I had already deleted old vista partitions (which had the bootloader for windows) and reformatted them to swap and ext4. Left with a unbootable system I did a live install from usb, partitioning the disks to keep the old Windows partition and put Ubuntu on a new one. The install succeeded, and Ubuntu now boots from my system using Grub2.

The problem is grub wont boot or find my windows partition. The following is the Boot Info Script, and the Windows 7 Partition i want to access is at sda5. The file system at sda2 is just an 18gb ntfs filesystem with a few movies/games on it.

tl;dr look at sda5 boot sector info
```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 283273216.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

```

So i guess my questions are; 
How do i resolve the boot sector and fdisk differences. 
And What location do i tell grub to look?

as my grub2 40_Custom file i have
```
menuentry "Windows 7" {
set root=(hd0,5)
chainloader +1
}
``` and have tried all of the possible number sets of root=(hd0,2) or (hd0,msdos2)
Nothing seems to work

Any questions welcomed

---

