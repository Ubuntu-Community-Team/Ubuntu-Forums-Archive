---
title: "Ubuntu wont boot"
date: 2010-07-07
forum: General Help
---

### Post by codypurdue on 2010-07-07
Hi, i'm having some major issues with my windows hard drive so I'm trying to load ubuntu on another hard drive. I'm running an Acer Aspire 8730 laptop. 

The HD i put ubuntu on was a new HD i purchased and installed. My original HD is still installed but it is failing. I used my girlfriends comp to burn ubuntu 10.04 LTS onto a dvd. I then put it in and selected try(which is how im posting this now) and then installed on the newer HD. Now when i try to boot up using the appropriate HD as the primary boot. When the computer turns on it has a flashing white line on a solid black background and will never leave that screen. 

Any ideas of whats going on and i can provide any other information needed. Thanks!

---

### Post by codypurdue on 2010-07-07
bump! I need help i can't find anything helpful!

---

### Post by energybeing on 2010-07-07
Try shutting the machine off and then removing the power cable from the old hard drive and then try turning it on and see if it will boot.

---

### Post by codypurdue on 2010-07-07
well that may be a problem because this is a laptop but i will attempt that. However, that will not totally solve all my problems because i am still looking to fix my windows HD, but i would be perfectly happy with Ubuntu for the time being.

---

### Post by Seanlol on 2010-07-07
please run the bootscript in my signature and post the results. Thanks.

EDIT: please don't do anything to your system before running this script. Doing so may worsen the problem, or disguise it.

---

### Post by energybeing on 2010-07-07
> **codypurdue said:**
> well that may be a problem because this is a laptop but i will attempt that. However, that will not totally solve all my problems because i am still looking to fix my windows HD, but i would be perfectly happy with Ubuntu for the time being.

Ah, both hard drives are internal hard drives though?

---

### Post by codypurdue on 2010-07-07
> **Seanlol said:**
> please run the bootscript in my signature and post the results. Thanks.

EDIT: please don't do anything to your system before running this script. Doing so may worsen the problem, or disguise it.

I ran the script, but i did remove my windows harddrive before doing so. This should not effect it because ubuntu is on another harddrive and i'm still getting the same system.
Here are the results:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   470,280,191   470,278,144  83 Linux
/dev/sda2         470,282,238   488,396,799    18,114,562   5 Extended
/dev/sda5         470,282,240   488,396,799    18,114,560  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        46ee7400-3ed1-4858-b9b5-dd005b8ee15a   ext4       Ubuntu                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        18af31cb-dd07-41f4-9465-2d0f65de126d   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by energybeing on 2010-07-07
You need to boot from an Ubuntu live CD and open a terminal and type 
```
sudo grub-install /dev/sda
```
This should fix your problem.

---

### Post by codypurdue on 2010-07-07
> **energybeing said:**
> You need to boot from an Ubuntu live CD and open a terminal and type 
```
sudo grub-install /dev/sda
```This should fix your problem.
I tried that and got this in my terminal.

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

---

### Post by Seanlol on 2010-07-07
See, this is what I'm talking about. You messed with your system before running the script when the MBR was on the Windows HD. This is why you can't go doing things willy-nilly. Try installing grub and see if that works.

EDIT: If grub won't install, put the Windows HD back in the PC and re-run the script.

---

### Post by energybeing on 2010-07-07
What is the output of 
```
sudo fdisk -l
```?

---

### Post by codypurdue on 2010-07-07
> **Seanlol said:**
> See, this is what I'm talking about. You messed with your system before running the script when the MBR was on the Windows HD. This is why you can't go doing things willy-nilly. Try installing grub and see if that works.

EDIT: If grub won't install, put the Windows HD back in the PC and re-run the script.
Well when i open up my disk utility and look at the HD it says that the Ubuntu HD was the MBR and that was when the windows HD was in.

---

### Post by codypurdue on 2010-07-07
> **energybeing said:**
> What is the output of 
```
sudo fdisk -l
```?
The output is:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001188b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29274   235139072   83  Linux
/dev/sda2           29274       30402     9057281    5  Extended
/dev/sda5           29274       30402     9057280   82  Linux swap / Solaris

---

### Post by oldfred on 2010-07-07
You have to tell grub which partition to find its files when you reinstall from a liveCD.

Install from LiveCD:
Find linux partition change sda5 if not correct or even change sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

If you reinstall your windows drive you may still have issues. You need to set in BIOS to boot the Ubuntu drive. Depending on drive order as plugged in sda may be sdb and windows may not like it. 50/50 odds.

---

### Post by Seanlol on 2010-07-07
> **codypurdue said:**
> Well when i open up my disk utility and look at the HD it says that the Ubuntu HD was the MBR and that was when the windows HD was in.\

And there's no way for me to know that without you running the bootscript before messing with your machine.

That also seems unlikely if what you say is true; and the Windows HD was already in the PC when you installed a new HD then installed Ubuntu to it. Windows is way too fussy about it's bootloader.

---

### Post by codypurdue on 2010-07-07
> **Seanlol said:**
> \

And there's no way for me to know that without you running the bootscript before messing with your machine.

That also seems unlikely if what you say is true; and the Windows HD was already in the PC when you installed a new HD then installed Ubuntu to it. Windows is way too fussy about it's bootloader.

This HD isn't "new". It was not in the computer when i got it but installed later. My windows HD is also entirely fubared and I cannot boot up in windows.

[QUOTE=oldfred]
You have to tell grub which partition to find its files when you  reinstall from a liveCD.

Install from LiveCD:
Find linux partition change sda5 if not correct or even change sda if  sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

If you reinstall your windows drive you may still have issues. You need  to set in BIOS to boot the Ubuntu drive. Depending on drive order as  plugged in sda may be sdb and windows may not like it. 50/50 odds.
[/QUOTE]
I'm not sure what to make of the first part of that, i'm incredibly new to linux and ubuntu.
However, i am 100% sure my BIOS were set to boot the linux HD first.

---

### Post by codypurdue on 2010-07-07
I'm trying to install grub and got this: 
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

When i look at my disk utility it says that sda1 is my filesystem and the master boot record. =/

---

### Post by oldfred on 2010-07-07
If you had two drives installed and then your boot would have been sda the windows drive and grub would normally install to the sda drive to allow it to boot and let you choose Ubuntu or windows. It would have then overwritten the windows boot loader part that is in the MBR.

You can restore that to the windows drive with a windows repair CD and run the command fixMBR.

Without having seen the full results.txt with the windows drive none of us can help you with windows problems.

---

### Post by codypurdue on 2010-07-07
> **oldfred said:**
> If you had two drives installed and then your boot would have been sda the windows drive and grub would normally install to the sda drive to allow it to boot and let you choose Ubuntu or windows. It would have then overwritten the windows boot loader part that is in the MBR.

You can restore that to the windows drive with a windows repair CD and run the command fixMBR.

Without having seen the full results.txt with the windows drive none of us can help you with windows problems.
Well i can reinstall the windows drive, but the drive is failing and will not boot up. I will install the drive and run the script again.

---

### Post by codypurdue on 2010-07-07
I put my HD's back to what they were before i changed a thing. My disk utility is now reading that i dont even have ubuntu installed >_< I'm about to throw this laptop out the window and not try to salvage it. However, i will run the script anyway just to see if it helps.
EDIT: Updated Results
             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    26,626,047    26,624,000  27 Hidden HPFS/NTFS
/dev/sda2    *     26,626,048   322,713,599   296,087,552   7 HPFS/NTFS
/dev/sda3         322,713,600   618,848,255   296,134,656   7 HPFS/NTFS
/dev/sda4         618,848,256   625,139,711     6,291,456  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        EAEE-EB49                              vfat       PQSERVICE                     
/dev/sda2        D8E226D9E226BB9E                       ntfs       Acer                          
/dev/sda3        621CD6221CD5F151                       ntfs       DATA                          
/dev/sda4        5A6EC1DC6EC1B155                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda4/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768 
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by oldfred on 2010-07-07
What did you do to your Ubuntu install? If you reinstall Ubuntu to sdb be sure to use the advanced button to install grub to sdb and change BIOS to boot the 250GB drive.

You need to run fixMBR to get windows in the MBR to start booting. If you had other problems the other commands may fix things. You should run the chkdsk on all windows partitions. 

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by codypurdue on 2010-07-08
> **oldfred said:**
> What did you do to your Ubuntu install? If you reinstall Ubuntu to sdb be sure to use the advanced button to install grub to sdb and change BIOS to boot the 250GB drive.

You need to run fixMBR to get windows in the MBR to start booting. If you had other problems the other commands may fix things. You should run the chkdsk on all windows partitions. 

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
Well the only problem with that is i dont have any installation disks. And i would like to completly isolate my two harddrives. I want nothing to do with the windows HD for now. I just want a clean install of ubuntu on my seperate HD.

---

### Post by oldfred on 2010-07-08
Your sdb is not showing anything. If it was a new install and you do not have anything to recover, I would just reinstall. Just be careful to use manual install if it sees the existing partitions. Or install to full disk if not. Use the advanced button to make sure to install grub to the Ubuntu install drive.

You can download win7 and Vista repair only disks.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

