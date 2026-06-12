---
title: "Ubuntu destroyed my RAID array!"
date: 2010-10-10
forum: General Help
---

### Post by Andras B. on 2010-10-10
Not sure where to put this, but I just came across a very strange phenomenom, and I'd like to share it.
 
I have 2, 500GB hdd's in RAID 0 (striping) configuration. I am using the motherboard's RAID controller. I have Windows 7 installed and working on this array.
 
I have downloaded the Ubuntu 10.04.1 ISO, burned it to CD-RW, and booted it. I pressed ENTER at the initial screen, selected the disc check option. It checked the CD, then said there were no errors, then the computer rebooted. Windows could no longer start, turned out the RAID array was somehow removed from the configuration, and the 2 hdd's were just single disks. I had to re-create the array, re-add the disks to get Windows (and my data) back.
 
I have made zero changes between I shut down Windows and booted the live CD.
 
It was very frustrating for a moment, I thought my data was gone for good, after just booting the CD. Not even into Ubuntu desktop, just the boot menu (and the disc check function). This is indeed disturbing, and may even be a serious bug.
 
Relevant system specs:
 
ASUS M4A78L-M LE motherboard
AMD 780L northbridge / AMD SB710 southbridge
using onboard RAID controller in 0 (striping) mode
2x SATA-II 500GB hdd's in the array
Official Ubuntu 10.04.1 32-bit ISO burned to CD-RW

---

