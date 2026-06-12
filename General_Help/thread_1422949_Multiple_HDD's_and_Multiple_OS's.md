---
title: "Multiple HDD's and Multiple OS's"
date: 2010-03-06
forum: General Help
---

### Post by loaba on 2010-03-06
Goal - have Ubuntu on one HDD and Win 7 on another
Sub-Goal - get rid of GRUB without adversely affecting Ubuntu install


I have three HDD's on my system; one contains Win 7 Pro (no complaints, love it), one is for storage (NTFS) and the third has Ubuntu on it (aside from the wireless issues and DVD playback issues, I love it as well).

All three drives are internal, but the Ubuntu drive is a special case. It's installed in a cradle that resides in an external bay. The Ubuntu drive can be turned on and off at will. I don't need GRUB (which will only confuse my fair lady).

So, if I run Win 7 recovery and "repair" the mbr, what will that do to the Ubuntu drive (which will be set as the first boot device in BIOS)? Will it boot per normal when the cradle is powered up, or will it be looking for GRUB?

---

### Post by Intrepid Ibex on 2010-03-06
Requires a bit thinking because you have so many HDD's (notice the word _bit_). When you restore the win 7 bootloader with the dvd, it will overrun the first HDD's MBR, which you set in BIOS (which is the Ubuntu one from the looks of it).

Nothing will happend to ubuntu itself - when you don't have the drive on, it will read from the next HDD's MBR - if it has grub, it will read from that.

I might also be wrong in some points, I have no experience from multiple HDDs.

---

### Post by oldfred on 2010-03-06
When you repair your windows make sure you have set that drive to first in BIOS. Is your grub installed in the external or in the internal.

With multiple drives I like to run this script for my own information before and after I make any configuration changes so I can be sure where things are installed and what versions they are.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

If you want help understanding script you can post yours but I do not think it is necessary.

---

### Post by loaba on 2010-03-06
Currently in Windows right now, will DL the script after I reboot in to Lucid. In the mean time, I thought I'd clarify the situation.

Current BIOS Boot Order
DVDRW
STA3500630AS - Win 7 (internal)
STM3200820a - Ubuntu 10.4 (external/cradle)

After cleaning GRUB and Windows drive MBR
BIOS Boot Order
DVDRW
STM3200820a - Ubuntu 10.4 (external/cradle)
STA3500630AS - Win 7 (internal)

The second boot order makes it possible to turn the Ubuntu drive on/off at will, thereby eliminating the need for GRUB (I think). :)

---

### Post by loaba on 2010-03-06
And there is a fly in the ointment... :(

I should have known this. When I turn off the cradle, the drive stops reporting that it's there... When it's not present, what happens to the boot order? How do BIOS typically handle that sort of thing?


Boot Script

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:

---

### Post by oldfred on 2010-03-07
The BIOS should just skip that device and go onto the next device. The only issue can be if the software in the second disk is hard coded to be the third disk the number is now not correct and it will not boot. This was why grub was changed to UUID's, but new grub uses a combination of root & UUID?? Grub uses a map or mapdevice command to make windows on a second drive still think it is first so it can be booted either way. Direct boot it is first and works, grub boot switches drive order so windows is still first (even thought it is not).

---

### Post by loaba on 2010-03-07
Oldfred - you are quite right. I know this because I ran a simple test that I should have done to start with.

In BIOS, I set the Linux drive as 2nd boot device, in front of the Windows drive. When I take the Linux unit offline (via the external cradle), the Windows drive moves up into it's place (followed by the floppy).

I know the BIOS side will act in a way I want; what will Linux do if I scrub GRUB off of the Windows disk?

---

### Post by oldfred on 2010-03-07
You only need grub on the device you boot as it is best at chainloading or booting other systems. I like to have different operating systems on different drives if you have more than one drive and have that operating systems boot loader in that drive's MBR. Each drive could then boot on its own in  case one drive has problems.

Some go so far as to add an operating system to a pure data drive just in case they need to do recovery.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

