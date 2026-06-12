---
title: "can I recover files running from LiveCD?"
date: 2011-05-21
forum: General Help
---

### Post by ezcuincle on 2011-05-21
I been trying to figure out why after updating to the newest version of ubuntu the system didnt work anymore, but now my main concern is trying to recover files that I had on my computer, how can I do this?
and worry about fixing ubuntu later.

---

### Post by oldfred on 2011-05-21
From the liveCD you should be able to copy anything. 

Upgrade Guide/Issues Including 11.04 mörgæs
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

To make repairs be sure to have same version liveCD.
LIveCD needs to be 1.99 same version
[http://ubuntuforums.org/showthread.php?t=1751383](http://ubuntuforums.org/showthread.php?t=1751383)

To see if booting is the issue. It may also be video issues.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by ezcuincle on 2011-05-21
I was able to find some files, but those are the ones that I have on windows.  The computer is partitioned in windows and linux,  how can I get to the files I had on ubuntu and not the ones on windows?

---

### Post by ezcuincle on 2011-05-21
and this is the info I get: 

 ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
205 heads, 13 sectors/track, 43981 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   117,207,039   117,204,992   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B26442F46442BB3D                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
-------------------------------------------------
```

---

### Post by oldfred on 2011-05-22
You do not have it partitioned. You have wubi which is just a file inside the NTFS partition and uses windows to boot.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
nautilus /mnt

---

### Post by Rubi1200 on 2011-05-22
ezcuincle,
I already posted in your other thread on the same subject. Please don't start multiple threads; it dilutes community efforts to help you and others.

To repeat what I said in the other thread. You are missing the root.disk and need to try and recover it ti get your files back.

Thanks.

---

