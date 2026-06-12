---
title: "My Ubuntu Laptop suddenly didn't successfully boot"
date: 2011-01-15
forum: General Help
---

### Post by beesyell on 2011-01-15
I took a [video of my laptop screen as I was trying to boot it]("http://www.youtube.com/watch?v=AMTnX35hyls").  I've tried turning it off and on several times but still same thing  happens. What's happening? Will I be able to recover my files in there?

---

### Post by solar george on 2011-01-15
Have you tried booting with the older kernel (the third option in the list)?

---

### Post by beesyell on 2011-01-15
Yes, I've been trying to boot with the two of them alternately. TT_________TT

---

### Post by solar george on 2011-01-16
OK try booting off a live cd and see if you can access your files from there, I think you'll probably have to re-install but I'm rather afraid that your filesystem is severely damaged which would mean loss of files.

---

### Post by theasprint on 2011-01-16
Hi,

I would recommend you first posting something before you decided to reformat your PC.
I would want you to post the results of the bootinfoscript in this thread.

1. Boot from a LiveCD (that means Try Ubuntu without Changes) 
2. Have internet connection and go to the link below in my signature
3. Go follow the instructions in the bootinfoscript website and post the results (results.txt) in this thread
4. Use the [CODE] tags to put the results in a nice box.

The bootinfoscript will give an overview of your whole system to enable examining on what went wrong with your system

---

### Post by theasprint on 2011-01-16
Hi,

I would recommend you first posting something before you decided to reformat your PC.
I would want you to post the results of the bootinfoscript in this thread.

1. Boot from a LiveCD (that means Try Ubuntu without Changes) 
2. Have internet connection and go to the link below in my signature
3. Go follow the instructions in the bootinfoscript website and post the results (results.txt) in this thread
4. Use the [CODE] tags to put the results in a nice box.

The bootinfoscript will give an overview of your whole system to enable examining on what went wrong with your system

---

### Post by TheHackOps on 2011-01-16
I had this problem as well, This normally happens when the mount point in fstab is /dev/sda1 or w/e.

My solution was to change the mount point to UUID= and the hard drive that was meant to mount :) hope i helped maybe someone can clear this up for his as i am going to bed soon and its 2am

---

### Post by solar george on 2011-01-16
> **TheHackOps said:**
> I had this problem as well, This normally happens when the mount point in fstab is /dev/sda1 or w/e.


Thats interesting, do you also get the kernel trace (the bit before --[ end trace ...) when that happens?
Dropping into busybox can be the result of several different problems with the root file system though (and I think you mean in the grub settings since the kernel can't read /etc/fstab until it has a working /)

---

### Post by beesyell on 2011-01-28
> **theasprint said:**
> Hi,

I would recommend you first posting something before you decided to reformat your PC.
I would want you to post the results of the bootinfoscript in this thread.

1. Boot from a LiveCD (that means Try Ubuntu without Changes) 
2. Have internet connection and go to the link below in my signature
3. Go follow the instructions in the bootinfoscript website and post the results (results.txt) in this thread
4. Use the ```
 tags to put the results in a nice box.

The bootinfoscript will give an overview of your whole system to enable examining on what went wrong with your system

here it is:

[CODE]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   625,139,711   624,932,864   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       ec6108aa-7093-40cc-a025-54ffbaafa77b   ext4                                     
/dev/sda1        025ECAB25ECA9DB3                       ntfs       System Reserved               
/dev/sda2        18D2CEA1D2CE830C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by beesyell on 2011-01-28
> **TheHackOps said:**
> I had this problem as well, This normally happens when the mount point in fstab is /dev/sda1 or w/e.

My solution was to change the mount point to UUID= and the hard drive that was meant to mount :) hope i helped maybe someone can clear this up for his as i am going to bed soon and its 2am

how do i do that?

---

