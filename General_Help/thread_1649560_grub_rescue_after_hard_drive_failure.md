---
title: "grub rescue after hard drive failure"
date: 2010-12-20
forum: General Help
---

### Post by BSummers on 2010-12-20
dual boot ubuntu / windows on seperate drives

ubuntu drive fails today and now boots saying 

cannot find device (id) 
grub rescue>

what do i do next?

---

### Post by BSummers on 2010-12-20
to be clear i need to get back into my windows install as easily as possible

---

### Post by oldfred on 2010-12-20
Were you booting the windows drive or the Ubuntu drive? Generally it is best if grub is installed to the Ubuntu drive and you set that to boot in BIOS. Then you still have the windows boot loader in the windows drive and can boot that anytime with either the one time boot key (f12 on my system) or change BIOS.

To see how your system was set up:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

You may just need to reinstall a windows boot loader to the windows drive. But to be able to give specific instructions we need boot script's results.txt. What version of windows and do you have a Ubuntu liveCD ot Windows repairCD?

---

### Post by BSummers on 2010-12-20
I would guess it was installed to the windows drive as the ubuntu drive is no longer in the machine and grub is still coming up. I will try to run the bootinfo from a live cd and post the results

---

### Post by BSummers on 2010-12-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

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
Disk identifier: 0x00095074

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed83ed83

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        68DEE5FE45570C92                       ntfs       TwoFiddy                      
/dev/sdb1        26FCC46EFCC439B7                       ntfs                                     
/dev/sdc1        3CAED1556DFF4DCD                       ntfs       WD                            

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/WD                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/26FCC46EFCC439B7  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/TwoFiddy          fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
```

---

### Post by oldfred on 2010-12-20
Have you tried booting from sdc? It shows a windows boot loader.

Your install of XP ini sdb thinks it is the first drive.
multi(0)disk(0)[COLOR=Red]rdisk(0)[/COLOR]partition(1)\WINDOWS

Do not know if that would be an issue of not.

If you have an XP cd you can reinstall a XP boot loader, but with multiple drives I do not know for sure what drive it will install to.
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
FIXMBR  C:

It may be better/easier to install the Lilo bootloader. It works just like windows in that it looks for the boot flag and jumps to that partition to continue booting. 

Confirm that sdb is still windows drive with liveCD.
```
sudo fdisk -l
```
Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by katykat on 2010-12-20
Google for MBRFIX for Win. 

Much simpler. 

Fix the MBR, and good to go.

---

### Post by BSummers on 2010-12-20
lilo did the trick like a champ!

thanks for your help

---

