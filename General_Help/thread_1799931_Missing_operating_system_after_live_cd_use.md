---
title: "Missing operating system after live cd use"
date: 2011-07-08
forum: General Help
---

### Post by lesnik on 2011-07-08
Hello,
I was playing a bit with a 10.04 live cd and persistence on a small usb stick. I did that on a HP Probook 4510s with windows 7 installed. Testing the persistence, I changed the desktop background and tried to install a small package, about 14MB extra space was reported to be used. My usb stick is 512mb. Suddenly it says there's no more space. After that I rebooted with persistence and half way through loading it stopped saying there's no more space, again. I decided to call it quits and reboot it back to win 7, but doing that just left me with the message "missing operating system". I have no clue as to how it happened, since I did nothing with the hard drive. Any ideas?

thanks

---

### Post by Quackers on 2011-07-08
Take out the usb stick and shutdown completely. Leave it for 1 minute then try to boot from the hard drive like normal.
Which boot device is set to boot first in your bios? Check that.

---

### Post by lesnik on 2011-07-08
Thanks for the reply. It's been off for about half an hour with no usb stick, when I turn it on it's still the same. The first boot device is cd drive.

---

### Post by Quackers on 2011-07-08
Is there a cd in the drive?
Is the hard drive second boot device?

---

### Post by lesnik on 2011-07-08
I've taken everything out and yes, hd is the secod boot device.

---

### Post by Quackers on 2011-07-08
All I can suggest is that you go into your bios (not the one-time key press) and choose the option to reset bios to default values then try again.
If that still has no effect you will need to boot from an Ubuntu live cd/usb and select "try Ubuntu" then go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example
```
 cd Downloads/boot_info_script060
```

if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by lesnik on 2011-07-08
I've already tried resetting bios. Here's the RESULTS.txt:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   102,402,047   102,195,200   7 NTFS / exFAT / HPFS
/dev/sda3         102,402,048   976,769,023   874,366,976   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        dc30c36f-4d83-4983-8a31-069247d58b90   ext2       casper-rw
/dev/sda2        FC98884D988807FA                       ntfs       
/dev/sda3        1CBEB24ABEB21BE8                       ntfs       Local Disk

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
--------------------------------------------------------------------------------


```

---

### Post by lesnik on 2011-07-08
Reinstalled windows. Seemed like the fastest and easiest way. Nevertheless, thank you very much for your time.

---

