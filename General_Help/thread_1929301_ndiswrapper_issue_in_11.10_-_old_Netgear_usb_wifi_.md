---
title: "ndiswrapper issue in 11.10 - old Netgear usb wifi adapter"
date: 2012-02-21
forum: General Help
---

### Post by nux_guy22 on 2012-02-21
I recently installed Ubuntu 11.10 on a desktop machine I had laying around, and I'm working on getting a very old Netgear WPN111 usb wifi adapter to work. I have scoured the forums for a few hours looking at various guides, and was able to find some helpful information. I followed this guide: [http://only4geeks.net/?p=37](http://only4geeks.net/?p=37)  extensively to get ndiswrapper installed.

I now have ndiswrapper installed (including the graphical version in Ubuntu Software Center). I have downloaded the latest 64 bit drivers from Netgear (installed them in Windows and extracting the .inf and other files later). Using the guide linked to previously, I installed the correct .inf file. After following the rest of the steps and restarting, the wireless card still won't detect any networks. However, I now have a message stating "wireless card not read; firmware not found" in my connection manager. 

I noticed in that guide that configuration info for ndiswrapper was previously stored in /etc/modprobe.d/ndiswrapper.conf.  However, such a file is no longer created when following the steps in that guide. Instead, ndiswrapper now appears to store configuration information in /etc/modules.conf.

Using ndiswrapper 1.56. Terminal: "ndiswrapper -l" lists the card as driver installed and present. 

Any help would be greatly appreciated.

---

### Post by bluexrider on 2012-02-22
Found this for you

[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

[B] 	 Complete tutorial on how to set up Netgear WPN111  

hope it works 
[/B]

---

