---
title: "Windows won't work after partition"
date: 2011-04-25
forum: General Help
---

### Post by ninja cat 09 on 2011-04-25
Recently I had some issues with windows so I had my computer formatted and had windows XP and ubuntu 10.10 installed. 
Seeing that the partition space for ubuntu was too small I attempted to fix this with gparted. I unmounted the windows partition and made a 30 GB partition to expand the ubuntu partition, I was unable to join them and instead started using it as a removable drive, mounting it every time I use it. 
After the partition Windows stopped working (whenever I attempt to access it from GRUB I am asked if I want to enter windows normally or in safe mode then I am redirected to GRUB).
Here is the listing of current partitions, /dev/sda1 is supposed to be windows.
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda80da80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8561    68761568+   7  HPFS/NTFS
/dev/sda2           12386       14594    17737729    5  Extended
/dev/sda3            8561       12385    30720000   83  Linux
/dev/sda5   *       12386       14594    17737728   12  Compaq diagnostics

Partition table entries are not in disk order

Disk /dev/sdb: 4008 MB, 4008706048 bytes
61 heads, 21 sectors/track, 6112 cylinders
Units = cylinders of 1281 * 512 = 655872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ff48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        6111     3912704    b  W95 FAT32
Also, when I write 
```
sudo cfdisk
```in the terminal I get
> FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylind
                          Press any key to exit cfdisk
I am sorry if this is lacking details, I am a complete ubuntu newbie, If there is anything missing please tell me so I can add it. You're help is greatly appreciated.

---

### Post by frogotronic on 2011-04-25
Did you use gParted from within Ubuntu, or the LiveCD?

---

### Post by matt_symes on 2011-04-25
Hi

Please run the bootscript in my signature. It will tell us more abvout your current setup.  The instructions are on the page.

Post the resulting file between code tags. They are the # button next to the quote button.

Kind regards

---

### Post by Sun.Dial on 2011-04-25
Hi,
The script mentioned above gives a great deal of info about what is going on, so please do try it out.
Also, you might try downloading Super GRUB2 Disk 
([http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)) burning it to a CD. Boot from it and it will detect OSs on your HDD and let you choose which to boot from.
Good luck

---

### Post by ninja cat 09 on 2011-04-28
Cement Head: I used gparted from within ubuntu.

Matt: here are the results.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
```

---

### Post by techunit on 2011-04-28
You need to do this from the disk as partitioning your drive while accessing it is a bad idea. Reinstalling grub is a good idea to.

As for grub reinstallation you can look here

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by frogotronic on 2011-04-28
[QUOTE=ninja cat 09;10731692]Cement Head: I used gparted from within ubuntu.

[COLOR="Red"]**Ouch!**[/COLOR]   ](*,)

As a rule of thumb, never adjust your main HDD using gPARTED when gPARTED is running from an O/S that is booted from that HDD.

In other words, if a drive is mounted - don't adjust it using gPARTED.  If you wish to do this in the future, use gPARTED LIVE CD.  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

**To fix your situation you need to (i) set-up your partitions the way you intended them to be, and (2) re-install the GRUB2 (bootloader):**

**_In order:_**

1) Download the gPARTED ISO and burn a LIVECD.  Boot from that LIVECD and fix your partitions the way you want them.

2) Reinstall GRUB2 using a LIVECD of Ubuntu (your variant): [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

- CH

---

### Post by oldfred on 2011-04-28
If it is a partition table issue, that can be fixed or if you just need to run chkdsk from a windows CD on sda1 that may be the issue.

You did not post the entire boot script so we could see the details of your partition table and if it has overlapping issues.

You may want to back up partition table now. and copy it to another device.

Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

---

