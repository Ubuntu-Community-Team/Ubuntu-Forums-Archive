---
title: "Printing"
date: 2010-07-07
forum: General Help
---

### Post by louis.roux on 2010-07-07
I have a HP-Laserjet3015 that I have been using with no problems.  All of a sudden it will not print.  It has a status message that says it may not be connected.  I checked all connections and they are fine.  I deleted the printer from my computer, unplugged the usb cable, turned the printer off and rebooted my computer.  Then I plugged everything back in and turned my printer on and it found the driver and said it was ready to print.  But when I try to print nothing happens and then it gets that status message again.  PLEASE HELP.  I have important docs to print for work.

---

### Post by hyperboloid on 2010-07-07
Same here. Exactly the same printer model, exactly the same issue. I'm running 10.04 and this printer has worked great for years on Ubuntu. I think there was a CUPS update recently, what got broken?

---

### Post by hyperboloid on 2010-07-07
OK, seems like I found a fix, or at least a workaround.  My printer is connected via USB cable, which might be a necessary precondition for this workaround.  On the other hand, it may be that the problem lies with the USB software; specifically with the libusb package (see last paragraph). If so, you might not be having this issue unless you connect via USB. 

Here's my workaround: Try going to **System -> Administration -> Printing** and right click on the printer, and select **Properties**. Under **Device URI** click on the **Change...** button and then click on the **Connections** triangle, and select **USB** instead of **HPLIP**. Then click on **Apply** and it should start working again. 



By the way, when I poked around a bit by typing > cat /var/log/cups/error_log  in a terminal, I saw loads of error messages like this one 
>  D [07/Jul/2010:17:27:05 -0500] [Job 105] prnt/backend/hp.c 752: INFO: open device failed stat=21: hp:/usb/hp_LaserJet_3015?serial=00CNBM099707; will retry in 30 seconds...

and after a bit of Googling around I found this bug report [https://bugs.launchpad.net/hplip/+bug/595650]("https://bugs.launchpad.net/hplip/+bug/595650") that *might* be related. See also the thread at  [http://ubuntuforums.org/showthread.php?t=1516181]("http://ubuntuforums.org/showthread.php?t=1516181") which has some other suggestions, and might be related.

---

### Post by optimisticyet on 2010-07-12
I've had a similar experience, and the fix suggested by **hyperboloid**  worked for me too. Detailed conditions follow, below.

I have an HP LaserJet 1320 printer directly connected to a USB socket on  my desktop PC. It's been working fine, under Ubuntu 10.04 (Lucid), but  after accepting a recent update to *cups*, I started to get the  "printer may not be connected" message that **louis.roux** describes.  My version of *cups* reported by Synaptic Package Manager is now *1.4.3-1ubuntu1.2*  

I notice that Synaptic Package Manager would allow me to reinstall the  previous version (*1.4.3-1*) but I would have to use the "Force"  option and there is a warning that there may be possible broken  dependencies. So I'm glad there's a simpler solution.

---

