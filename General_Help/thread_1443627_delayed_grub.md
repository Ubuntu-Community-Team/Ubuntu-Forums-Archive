---
title: "delayed grub"
date: 2010-03-31
forum: General Help
---

### Post by littleoak on 2010-03-31
Hi, I have just installed ubuntu 9.10  on its own HDD  the the computer has another HDD with windows xp. The problem is ubuntu has removed the MBR from windows and installed some other file on the windows HDD which points to Grub wherever it is. this takes forever about 45 secs. I need to boot straight into Grub or use f11 boot menu options.

Can anyone help me put this right ?:-({|=

---

### Post by ajgreeny on 2010-03-31
I had this happen when I tried Mint8 some time ago, with the Mint grub on the sda MBR and Mint on sdb.  It took a long time for the system to open the grub menu, but when it did open everything from that point worked as expected.

I found a few reports of this happening when the OS was on a separate disk, not just partition, to the MBR, and so I put grub2 from Mint onto sdb and all was well from then; grub appeared almost instantly after the "starting grub" appeared on screen at boot.  I just needed the BIOS to boot to sdb, hd1 in my BIOS, of course to use Mint's grub.

Since then I have not been able to replicate the same thing happening, as I currently have grub2 on both disks, one from Ubuntu 9.10 on sda and from Mint8 on sdb, but both work properly irespective of which grub or OS I boot to, and I actually have 4 different linux OSs on the two disks.

---

### Post by 2hot6ft2 on 2010-03-31
From the [Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275") section 17

> Grub 2 Hangs 10-30 Seconds between Grub 2 Loading and Menu Display.
This is a known bug that can be caused by GRUB 2 and /boot being loaded on different partitions. To fix the problem, run

```
sudo dpkg-reconfigure grub-pc
```

Select to load Grub 2 on the same device as the /boot partition. In your system BIOS, change the drive to boot from first to the drive with the /boot partition.


---

### Post by littleoak on 2010-03-31
Thanks that seems to be a similar problem. here is the results text from the boot info script. I think the answer is in here rhe question is can you help me fix it.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=1e7577b7-b71e-48af-ae47-2716a636385d)/boot/grub.
 => Grub  is installed in the MBR of /dev/sdb and looks at sector 19009 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/grub.conf.




sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

---

### Post by littleoak on 2010-03-31
thanks for that, I tried but it doesent seem to work. did that to both drives but when I switched drives in the bios to boot from sdb thats where linux is the system says boot record OK then just hangs. should I try setting the boot flag on that drive ?.

---

### Post by littleoak on 2010-03-31
:popcorn:Thanks for all your help the problem seems to be fixed now.

---

