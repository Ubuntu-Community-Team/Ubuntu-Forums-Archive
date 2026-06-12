---
title: "Ubuntu cannot boot due to corrupted file"
date: 2010-12-27
forum: General Help
---

### Post by cgong on 2010-12-27
[I]Hi,

I have a virtual ubuntu machine (wubi) under windows 7. Recently, I have been unable to boot ubuntu because the file [/I]*/[I]ubuntu*/*winboot*/*wubildr*.[/I][I][I]mbr appears to be corrupted. Windows 7 boots fine. How can I repair my ubuntu without loosing my files or how can I retrieve my user files before I install ubuntu again?

Thanks,

 cgong[/I]
[/I]

---

### Post by Ir0nMa1deN on 2010-12-27
By virtual machine I assume you mean you're using VirtualBox or some similar software, am I correct? If so, I would get rid of that cause it's more trouble than its worth (trust me I've done it before, virtual machines are slow and very hard to get working)

---

### Post by bcbc on 2010-12-27
See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for a fix. You didn't say but I'm going to assume that you have 10.04.1 Ubuntu and you recently ran updates. Then that would be Problem #2, Solution #1.

PS that thread has links to a download (ext2read) that you can use to extract data from the root.disk. If you find it too time consuming to go through all the steps to fix.

---

### Post by cgong on 2010-12-29
> **bcbc said:**
> See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for a fix. You didn't say but I'm going to assume that you have 10.04.1 Ubuntu and you recently ran updates. Then that would be Problem #2, Solution #1.

PS that thread has links to a download (ext2read) that you can use to extract data from the root.disk. If you find it too time consuming to go through all the steps to fix.

I tried Problem #2, Solution #1 as you suggested and I get the following in response:

sudo mkdir /media/win 
sudo mount /dev/sda**2** /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
/media/win/ubuntu/disks/root.disk: No such file or directory 



 /dev/sda2 IS my Windows partition and mounts without problems. 

CHKDSK under Windows returns no errors.

My installation is ubuntu 10.10 inside Windows.

Any suggestions? Thanks for the tips!

---

### Post by Rubi1200 on 2010-12-29
Hi and welcome to the forums :-)

If you used a LiveCD/USB to run the previous commands, please boot the computer with it again, choosing to try not install.

Post the results of the boot info script linked at the bottom of my post.

Thanks.

---

### Post by cgong on 2010-12-29
Hi,

I used a proper ubuntu 10.04 installation on the computer to run the boot info script. Here are the results:

 ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr /ubuntu/disks/swap.disk

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 HPFS/NTFS
/dev/sda2           2,459,648   132,572,944   130,113,297   7 HPFS/NTFS
/dev/sda4         234,977,278   488,396,799   253,419,522   5 Extended
/dev/sda5         465,726,240   478,003,679    12,277,440  83 Linux
/dev/sda6         478,017,536   488,396,799    10,379,264  82 Linux swap / Solaris
/dev/sda7         234,979,983   465,726,239   230,746,257   7 HPFS/NTFS


blkid -c /dev/null:

I hope this is of any help. Thanks a lot!

cgong

---

### Post by Rubi1200 on 2010-12-29
Not sure what is going on, but you appear to be missing files on sda2.

It should look like this for a normal Wubi install:
```
/bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk
```

As bcbc mentioned above, you could try recovering files using [ext2read]("http://ext2read.blogspot.com/")

---

### Post by bcbc on 2010-12-29
the root.disk is missing.

Sometimes windows can move this to a hidden folder c:\FOUND.??? if it has to recover it from corruption. Search your computer for it.

If you can't find it then there is nothing you can do to recover Ubuntu or the files on it.

---

### Post by cgong on 2010-12-29
Ext2read only brings up the partition with the working 10.04 installation. Well, I guess it's curtains for my 10.10 files then. Certainly learned something. Thanks everyone for the help! See you around!

---

### Post by bcbc on 2010-12-29
> **cgong said:**
> Ext2read only brings up the partition with the working 10.04 installation. Well, I guess it's curtains for my 10.10 files then. Certainly learned something. Thanks everyone for the help! See you around!

ext2read won't automatically pick up a root.disk. You have to steer it in the right direction. I'm just adding this in case you though that the lack of it in ext2read means it's gone.

I have seen a couple of threads in the past month where it appears the root.disk has spontaneously disappeared - but I have no idea how this may occur.

---

