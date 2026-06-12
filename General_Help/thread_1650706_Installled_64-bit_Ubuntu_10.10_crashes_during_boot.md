---
title: "Installled 64-bit Ubuntu 10.10 crashes during boot-up."
date: 2010-12-22
forum: General Help
---

### Post by jsvensso on 2010-12-22
Hi,

I installed 64-bit Ubuntu 10.10, but it crashes during boot-up.
Installation was done through wubi 30GB option.
However live CD worked fine.

Machine used: HP Pavilion dv3.

Any suggestions?

---

### Post by sikander3786 on 2010-12-22
Hi.

Was 10.10 working ok previously and you applied some updates and it got borked?

Is Windows booting fine?

Depending on those queries,  problem # 1 or problem # 2 from following thread would apply.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
courtesy of forum member *Rubi1200* and others.

And once the issue is fixed, don't forget to apply the "Permanent Fix" from the link above in order to save you troubles later.

---

### Post by jsvensso on 2010-12-22
Thanks for the great link.

However I doubt that is my problem, since it try to boot but failing with a null pointer exception.

---

### Post by garvinrick4 on 2010-12-22
Wubi uses Windows bootmanager and puts a entry in with wubildr in it. Do not know
if you are using xp/vista or 7 but look for entry in your Windows boot manager to
see if is there. If is in the grub-menu then is in boot-manager and will need the fixes
in website given to you. Take a peak if "Vista or 7" is bcdedit at command line dos.

---

### Post by sikander3786 on 2010-12-23
And you can also post the output of bootinfoscript and let us take a look at your boot.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by jsvensso on 2010-12-23
Here is my result:

                Boot Info Script 0.55    dated February 15th, 2010                    

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
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


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   937,402,367   936,992,768   7 HPFS/NTFS
/dev/sda3         937,402,368   976,560,127    39,157,760   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       963c631a-7242-4285-b262-6f17cbb907a6   ext4                                     
/dev/sda1        6C4A88D04A88990A                       ntfs       SYSTEM                        
/dev/sda2        405A58045A57F55E                       ntfs                                     
/dev/sda3        54D8A9F5D8A9D590                       ntfs       RECOVERY                      
/dev/sda4        94F1-7027                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by Rubi1200 on 2010-12-23
Hi,
sikander3786 asked me to have a look and offer some ideas.

Here is what you can try:
Mount the Wubi install from a LiveCD and run a file-system check.

Note that this must be done from the LiveCD and I cannot guarantee it will work.

```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```

Post back with errors and/or other issues you encounter.

If this works you should be able to boot into Ubuntu again.

---

### Post by jsvensso on 2010-12-27
Hi,

Thanks for your support, however that did not work either:
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/media/win/ubuntu/disks/root.disk: återhämtar journalen
/media/win/ubuntu/disks/root.disk: rent, 129317/1905008 filer, 661979/7614464 block
ubuntu@ubuntu:~$ 


However when booting wubi ubuntu it still crashes.

And the part of the visible error message says something like:
BUG: unable to handle NULL pointer dereference at
IP: [<ffffffffa00523c6>] ips_detect_cpu+0x76/0x1d0 [intel_
PGD 1486ca067 PUD 1486c9067 PMD 0
Oops: 0000 [#1] SMP

---

### Post by jsvensso on 2010-12-27
Seems to boot (sometimes atleast) without ui if I in grub edit and add:
acpi=off noacpi

---

