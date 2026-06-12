---
title: "Graphics Driver"
date: 2011-08-30
forum: General Help
---

### Post by sillyoldman on 2011-08-30
Hi guys. I am posting this from a win 7 PC. I have 2 Ubuntu 11.04 to install the a Intel dual core machine. They are 32bit and 64bit.
1 Which do you recommend. 32 or 64 ?
2 I have an ASUS EAX1900. Unfortunatley I seem to be unable to find a driver for it for the said operating system.
Any Ideas ?
Being s new Linux user I will probably be coming tO this site for ideas and information. So please bare with me if it seems silly, all help would be gratefully received. THANK YOU guys.
 From sillyoldman.

---

### Post by seawolf167 on 2011-08-30
Welcome to the Forums!

1. Install the x86_64 (64bit) OS if your machine supports it.
2. The [X1900 XT ]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English")has moved to legacy support and should work just fine on your computer. You can get all your available drivers through the "Additional Drivers" program.

---

### Post by Frogs Hair on 2011-08-30
Hello sillyoldman

1. 32 bit is recommended on the Ubuntu website and I don't really know why . There are a number of threads about why that is so .  If you plan to use more than 4 Gb of memory you will need to install 64 bit . I have never had problems finding 64 bit compatible programs , but user experience may vary .

2. I have no experience with that graphics controller / card  . If there is no driver available in additional drivers you will have to wait for a member with more knowledge of that graphics controller / card .

---

### Post by Vesa Paatero on 2011-08-30
> **Frogs Hair said:**
> 
1. 32 bit is recommended on the Ubuntu website and I don't really know why . There are a number of threads about why that is so .  If you plan to use 


Well, at first 32 bits was the standard and 64 was experimental but I assume that the balance is constantly shifting toward 64 bits in terms of driver availability, support for different formats etc. Open source stuff can generally be compiled for either word size but with binary-only drivers there may be differences in availability. I don't know what the balance between 32 and 64-bit systems is at present but the direction of change should be clear.

Vesa

---

### Post by Mark Phelps on 2011-08-31
There will be NO drivers available for that video card in the Additional Drivers area.  Why? Because, as mentioned, your card has been moved to "legacy" status by AMD/ATI.

However, Ubuntu will install open-source drivers that will give youn perfectly good 2D graphics.  Just don't expect to run Games or anything else that requires hardware acceleration because it's not available anymore for that card.

Also, don't be tempted to rummage around looking for newer drivers -- because there aren't any.  Anything you find is likely to trash your display and put you through a LOT of work to restore the default open-source drivers.

---

