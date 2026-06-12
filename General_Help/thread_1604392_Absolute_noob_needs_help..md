---
title: "Absolute noob needs help."
date: 2010-10-24
forum: General Help
---

### Post by Snorton20 on 2010-10-24
Installed ubuntu today after installing a new hard drive off of a live  CD with ISO image to the new hard drive. Once it was done, it operated  fine. Until I shut it down. when i went to use the laptop again, it gave  me the following message:

GNU GRUB version 1.98+20100804-5ubuntu3
Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.
grub>

It won't boot ubuntu at all from either the hard drive or the ISO CD  again. It keeps on coming up to the above error message. What do I do?  Please help! please be patient with me. Thank you for guidance for a  complete noob.

---

### Post by garvinrick4 on 2010-10-24
> **Snorton20 said:**
> Installed ubuntu today after installing a new hard drive off of a live  CD with ISO image to the new hard drive. Once it was done, it operated  fine. Until I shut it down. when i went to use the laptop again, it gave  me the following message:

GNU GRUB version 1.98+20100804-5ubuntu3
Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.
grub>

It won't boot ubuntu at all from either the hard drive or the ISO CD  again. It keeps on coming up to the above error message. What do I do?  Please help! please be patient with me. Thank you for guidance for a  complete noob.
Do you have a install cd or usb. If so use Try ubuntu (makes it a live cd or usb) and open a terminal and go to this site.[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
Then download that script to your desktop make sure to desktop and then run this code in a terminal and will put a text file on desktop, post it to this thread. Takes 30 seconds or so. terminal is in

Applications /Accessories/ to terminal
 ```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by efflandt on 2010-10-24
For many computers you need to watch your BIOS splash screen (which comes up before grub) when you boot and see what key you need to press to select an alternate boot device (other than internal hard drive) regardless of what you set in BIOS boot order.  Often that key is F12 or Esc.  The reason it may have booted from the CD originally is because your new hard drive had no mbr on it.

You have given no information about your hardware.  Some older computers (like my older HP from 2004) do not like the new since 10.04 partitions on MB boundaries instead of cylinder boundaries.  In that case you may need to press any key when you see the keyboard initial keyboard graphic at the bottom of the screen of install CD and add **partman/alignment=cylinder** in the line that contains **quiet splash**.  Then boot to a live system, do **sudo swapoff -a** in a terminal, delete and recreate your partition(s) with **Gparted** (making sure that you have align to cylinder checked), then reinstall Ubuntu (selecting partitions you already created) in Advanced partitioning mode for / or whatever else (it will automatically find swap partition).  Or if you are not quite sure how to do the latter part just delete the partitions with Gparted and let the Ubuntu install set up partitions for you again using entire disk.

This is a release note about 10.04 (Lucid), but also applies to 10.10 (Maverick) [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)

---

### Post by Deorwin on 2010-10-26
> **garvinrick4 said:**
> Do you have a install cd or usb. If so use Try ubuntu (makes it a live cd or usb) and open a terminal and go to this site.[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
Then download that script to your desktop make sure to desktop and then run this code in a terminal and will put a text file on desktop, post it to this thread. Takes 30 seconds or so. terminal is in

Applications /Accessories/ to terminal
 ```
sudo bash ~/Desktop/boot_info_script*.sh
```


Ok so I just got this error and saw this thread and I did what you said and this is what I got (oh and i am running an HP dv2000 if that help?):

```
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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,394,751   488,187,904   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       f8fcb53f-cbb0-432c-972a-248bf225a62e   ext4                                     
/dev/sda1        EE4C1F054C1EC7EB                       ntfs       System Reserved               
/dev/sda2        CA2C21432C212BBF                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by Quackers on 2010-10-26
Deorwin, 
welcome to Ubuntu Forums.
You would be better served by starting your own thread. Your installation is different from the original poster's, as yours is a wubi install.
Make a new thread stating what has happened and on what hardware and which version of Ubuntu you have and whether it was an install or an upgrade. Also the boot script output is a good idea and I would ask you to show it there as well.

---

