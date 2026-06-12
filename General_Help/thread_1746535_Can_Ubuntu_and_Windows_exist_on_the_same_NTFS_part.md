---
title: "Can Ubuntu and Windows exist on the same NTFS partition?"
date: 2011-05-01
forum: General Help
---

### Post by dverebe on 2011-05-01
So I am reaching an unfortunate conclusion.  I asked this of google and got no straight response so I conclude that it is impossible.

taking a look at GParted with my 10.4 boot disk, I see 

/dev/sda1 NTFS 74GB boot flag

and

unallocated  unformatted 7.84GB no flag

So I assume that that 8gb used to be ubuntu.

In the process of trying to fix things, the computer no longer boots windows.

GULP*

whatdoidonow?!

[edit] yes, it is possible.  You installed Wubi. (or similar)

---

### Post by mynameisnotbob on 2011-05-01
It no longer boots windows? Can you still access the files from windows from the LiveCD? Also, what led up to both of them failing? Normally, Ubuntu and Windows can coexist pretty peacefully.

---

### Post by dverebe on 2011-05-01
Originally, the Windows Boot Loader would pass me off to GRUB and life was peaceful.

THEN.  Grub failed.  I should have recorded the original fail message.

So I re-installed GRUB (which overwrote the MBR) and now it just says "error:file not found"

and leadsd me to
grub rescue>

---

### Post by mynameisnotbob on 2011-05-01
Ohhh...I hate grub rescue. can you load normal module?
```
insmod normal
```
then put
```
normal
``` to activate it. Post and say if it works.

---

### Post by wilee-nilee on 2011-05-01
So from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us the info needed.

Do you have a install or recovery disc for the Windows? Also if you answer without the script, let us know at the least the info in this paragraph, including which windows.

---

### Post by dverebe on 2011-05-01
tried insmod normal from terminal on the live CD as both root and the default user. Both times it replied:

```
insmod: can't read 'normal': no such file or directory
```

---

### Post by dverebe on 2011-05-01
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        76C8E5BCC8E57B2F                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=c:\wubildr.mbr 
[operating systems] 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

---

### Post by dverebe on 2011-05-01
Doya think the filesystem lost it's "journal"?

---

### Post by wilee-nilee on 2011-05-01
> **dverebe said:**
> Doya think the filesystem lost it's "journal"?

Lets confirm that that is the whole script.

Bumps are limited to one per 24 hours, just so you know.

---

### Post by dverebe on 2011-05-01
1

---

### Post by dverebe on 2011-05-01
pre { font-family: "Liberation Serif"; }p { margin-bottom: 0.08in; }  ```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        76C8E5BCC8E57B2F                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; ;Warning: Boot.ini is used on Windows XP and earlier operating systems. ;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. ; [boot loader] timeout=30 default=c:\wubildr.mbr [operating systems] 
=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

```

---

### Post by wilee-nilee on 2011-05-01
You have stacked on top of each other the first post of the script, now I'm really confused lol, could you edit this last one, remove all but the code tags. Now open the gedit hit edit select all right click in the gedit and copy; then paste the text in between the code tags.

---

### Post by oldfred on 2011-05-01
You have wubi.

Wubi is a file inside the NTFS partition and boots from the windows boot loader. You do not install grub to the MBR but have to have windows boot loader in the MBR.

Use your windows repairCD to reinstall the windows boot loader.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by dverebe on 2011-05-02
So anywhoozen, I followed the above instructions which led to a repaired Windows 7... Then I remembered that yesterday, while I was organizing the files in the windows OS, I deleted a bunch of old files I didn't need anymore.  Except that some of them were Wubi.

Newb fail.  Thanks a lot again for all y'alls help.

---

