---
title: "wubi loop"
date: 2010-11-25
forum: General Help
---

### Post by iroquois on 2010-11-25
hello everyone,i have a ubuntu 10.04 wubi install.After doing updates through the update manager i can no longer boot into ubuntu.I choose ubuntu then the computer shuts down and i'm back at the "windows or ubuntu" choice screen.I can boot into windows but choosing ubuntu puts me into a loop where it shuts down then restarts at the choice screen.Can this be fixed?

---

### Post by Rubi1200 on 2010-11-25
Hi,
take a look here [this]("http://ubuntuforums.org/showpost.php?p=10159040&postcount=5").

Make sure you backup files before moving/copying them and that you use the right partition e.g. if it is not sda1, but sda2.

---

### Post by iroquois on 2010-11-26
ty Rubi for your time,i've looked at the links you posted.I was hoping for something simple.Wished there had been a warning about how wubi doesn't react well to updates.

---

### Post by wilee-nilee on 2010-11-26
> **iroquois said:**
> ty Rubi for your time,i've looked at the links you posted.I was hoping for something simple.Wished there had been a warning about how wubi doesn't react well to updates.

like the name my grandfather was a full member.

A easy answer it may be but we need to see the bootscript in my signature. Paste the text in to code tags by clicking on the # in the reply window panel and paste the text between. Without this script we are just plain guessing.

---

### Post by iroquois on 2010-11-26
```
File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    30,732,344    30,732,282  27 Hidden HPFS/NTFS
/dev/sda2    *     30,734,336   143,433,727   112,699,392   7 HPFS/NTFS
/dev/sda3         143,433,728   271,618,039   128,184,312   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 32 sectors/track, 959 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,825,439     7,825,408   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7d1e0070-67d0-4dee-8d46-7d72021867cf   ext2                                     
/dev/loop3                                              squashfs                                 
/dev/sda1        7E80AD5280AD1227                       ntfs       PQSERVICE                     
/dev/sda2        020857B90857AB05                       ntfs       ACER                          
/dev/sda3        5064374E643735D6                       ntfs       DATA                          
/dev/sdb1        4AB6-8602                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
unionfs          /                        aufs       (rw,relatime,si=8623c1ba)
/dev/sdb1        /initrd/mnt/dev_save     vfat       (rw,noatime,fmask=0022,dmask=0000,allow_utime=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet)
/dev/loop1       /initrd/pup_ro1          ext2       (rw,noatime,errors=continue)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)
/dev/loop3       /initrd/pup_z            squashfs   (ro,noatime)


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: initrd.gz
    ??GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi 
=============================== StdErr Messages: ===============================

losetup: invalid option -- a
BusyBox v1.15.0.svn (2009-07-25 18:23:53 GMT-8) multi-call binary

Usage: losetup [-o OFS] LOOPDEV FILE - associate loop devices
    losetup -d LOOPDEV - disassociate
    losetup [-f] - show

Options:
    -o OFS    Start OFS bytes into FILE
    -f    Show first free loop device

losetup: unrecognized option `--show'
BusyBox v1.15.0.svn (2009-07-25 18:23:53 GMT-8) multi-call binary

Usage: losetup [-o OFS] LOOPDEV FILE - associate loop devices
    losetup -d LOOPDEV - disassociate
    losetup [-f] - show

Options:
    -o OFS    Start OFS bytes into FILE
    -f    Show first free loop device

Found Wubi on sda2. But could not create a loop device

```

---

### Post by iroquois on 2010-11-26
the above are the results tx i got with the boot info script.I used puppy linux 431.The reason i'd like to have my wubi ubuntu install back is i have a lot of books and manuals i downloaded on there.Also i'm on a 2.9 kbps dial-up connection.It took a very long time to do the update manager updates.We're not to far away from "smoke signals" over here in the wilds of northern canada.It took me a good 6 months of on and off trying to get dial-up to work with ubuntu.Wished it had the same set-up for dial-up as puppylinux has.Good thing about difficulties is that they help you learn i guess.
Thanks for your help,i appreciate it

---

### Post by wilee-nilee on 2010-11-26
You left out some of the text.

---

### Post by iroquois on 2010-11-26
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    30,732,344    30,732,282  27 Hidden HPFS/NTFS
/dev/sda2    *     30,734,336   143,433,727   112,699,392   7 HPFS/NTFS
/dev/sda3         143,433,728   271,618,039   128,184,312   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 32 sectors/track, 959 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,825,439     7,825,408   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7d1e0070-67d0-4dee-8d46-7d72021867cf   ext2                                     
/dev/loop3                                              squashfs                                 
/dev/sda1        7E80AD5280AD1227                       ntfs       PQSERVICE                     
/dev/sda2        020857B90857AB05                       ntfs       ACER                          
/dev/sda3        5064374E643735D6                       ntfs       DATA                          
/dev/sdb1        4AB6-8602                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
unionfs          /                        aufs       (rw,relatime,si=8623c1ba)
/dev/sdb1        /initrd/mnt/dev_save     vfat       (rw,noatime,fmask=0022,dmask=0000,allow_utime=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet)
/dev/loop1       /initrd/pup_ro1          ext2       (rw,noatime,errors=continue)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)
/dev/loop3       /initrd/pup_z            squashfs   (ro,noatime)


=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: initrd.gz
    ??GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi 
=============================== StdErr Messages: ===============================

losetup: invalid option -- a
BusyBox v1.15.0.svn (2009-07-25 18:23:53 GMT-8) multi-call binary

Usage: losetup [-o OFS] LOOPDEV FILE - associate loop devices
    losetup -d LOOPDEV - disassociate
    losetup [-f] - show

Options:
    -o OFS    Start OFS bytes into FILE
    -f    Show first free loop device

losetup: unrecognized option `--show'
BusyBox v1.15.0.svn (2009-07-25 18:23:53 GMT-8) multi-call binary

Usage: losetup [-o OFS] LOOPDEV FILE - associate loop devices
    losetup -d LOOPDEV - disassociate
    losetup [-f] - show

Options:
    -o OFS    Start OFS bytes into FILE
    -f    Show first free loop device

Found Wubi on sda2. But could not create a loop device

```
not sure if i did this right wilee

---

### Post by wilee-nilee on 2010-11-26
Hold on you can get to windows but not Ubuntu I think if rubi1200's advice doesn't work then you may need some advice from a regular user who specializes in this.

I don't have the expertize in wubi.

---

### Post by iroquois on 2010-11-26
ok wilee,thanks for your time.

---

### Post by bcbc on 2010-11-26
In that link Rubi posted, the fix is to edit the grub.cfg as described. Copying the wubildr worked on the 10.10 upgrade but won't fix this current grub problem on 10.04.1 installs. (I just ran a test to confirm).

Unfortunately it's a pain, but if you can run the bootinfoscript, it shouldn't be too hard to edit grub.cfg.

Note that the fix is not permanent. I'm not aware of a permanent fix.

If you want to just copy data off the root.disk you can use a tool called ext2read from windows.
If you get your wubi booting by editing the grub.cfg, then you will probably have to apply the workaround everytime you run 'sudo update-grub' or install/remove a kernel.

Hope that helps...

PS avoid updating packages grub-pc and grub-common with wubi installs.

---

### Post by iroquois on 2010-11-27
i've tried to access the root disk using ext2IFS .Not working.The root disk is in a ntfs partition and i'm guessing that ext2IFS only works on  extension 2 or 3 file systems.Think i'd need someway to open and read a DISK File(.disk),which is the file type my root disk is.

---

### Post by bcbc on 2010-11-27
Ext2read works - you just point it at the file c:\ubuntu\disks\root.disk.

If that doesn't work then there is probably some issue with the root.disk. Oh I just checked the end of the bootinfoscript and there are errors creating the loop device, so there probably is an issue with it.

Standard things to try are running chkdsk (My computer, right click on drive containing wubi (c: ?), Properties, Tools, Check disk for errors, Fix automatically). This will require a reboot.

Then if still not happy, boot a live CD and run fsck on the root.disk:
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```
Afterwards, try
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```
If that worked, browse it:
```
nautilus /mnt
```

Was there something else that happened after running updates? Maybe a hard shutdown?

---

### Post by iroquois on 2010-11-27
i don't remember doing a hard shutdown,anyhow i'm back on ubuntu.Did a real dual install.Sure had to scratch my head a lot,go through my pile of old documents and do a lot of trial and error to get dial up to work!! I left the wubi install right where it was so i'll be going back there to try out your suggestions bcbc.
Right now i've developped a severe case of "computerbuttitis.Mother nature just provided the cure,about a foot of snow to shovel!!! lol Thank you all for your patience and help.I should be alright now.

---

### Post by bcbc on 2010-11-29
> **iroquois said:**
> i don't remember doing a hard shutdown,anyhow i'm back on ubuntu.Did a real dual install.Sure had to scratch my head a lot,go through my pile of old documents and do a lot of trial and error to get dial up to work!! I left the wubi install right where it was so i'll be going back there to try out your suggestions bcbc.
Right now i've developped a severe case of "computerbuttitis.Mother nature just provided the cure,about a foot of snow to shovel!!! lol Thank you all for your patience and help.I should be alright now.

Cool. A direct install should have less issues to deal with. Getting outside is good too :)

---

