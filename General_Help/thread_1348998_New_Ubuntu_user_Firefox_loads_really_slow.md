---
title: "New Ubuntu user: Firefox loads really slow"
date: 2009-12-07
forum: General Help
---

### Post by thedarthraider on 2009-12-07
Hello. This is my first post.  I downloaded and installed Ubuntu on my older laptop as a boot option.  The problem I'm having is that Firefox performs poorly compared to the Firefox I have in XP.  I took a look at this post,[http://ubuntuforums.org/showthread.php?t=296443](http://ubuntuforums.org/showthread.php?t=296443) but it does not make sense to me.  I really want to like Linux, but my first experience is not starting out well.  Also I think it seems like it takes too long to boot also.  Any assistance is greatly appreciated.

---

### Post by mbrowning2000 on 2009-12-07
Are you fully updated? **System>Administration>Update Manager**

Secondly, What are your Hardware Specs? (How much RAM, What graphics chip, ect..)

---

### Post by thedarthraider on 2009-12-07
Dell Inspiron b120
1.4 Celeron M
489 mb

I'm updating now

---

### Post by Bradj47 on 2009-12-07
> **thedarthraider said:**
> Dell Inspiron b120
1.4 Celeron M
489 mb

I'm updating now
Wow, not much RAM at all and the processor is definitely below average. There's your explanation for why it loads slow. Mine also loads slower than on Windows, but I assume that's because Mozilla has more developers for Windows than for Linux. If you don't like Ubuntu, try OpenSuSE. I loved it when I tried it. The only problem is the application support. I really didn't like YaST and you had to compile from source most of the time because .deb packages don't work with SuSE.

---

### Post by Spaarkplug on 2009-12-07
Um. That is the reason why your Firefox is slow. There is a very high hardware impcompatability. And there is not enough RAM in your system either. If you do not want to spend money on hardware upgrade then in that case you can try using ArcLinux. Its much much different from using Ubuntu, I agree, but it has a very small footprint. And also it is known to boot incredibly fast. In my machine it boots to commandline in 3 secs, and to its GUI in 8.5 secs.
I personally use Ubuntu myself, but boy ArcLinux is faaaast. Installing packages is different, its a rolling release, and there is a lot of manual steps you need to do before your ArcLinux machine is useworthy.
-Spaark.

---

### Post by thedarthraider on 2009-12-07
If I added some ram say to 1gb would it run Ubuntu well?  I'm just amazed at how slow it runs compared to windows xp on this same machine.

---

### Post by mbrowning2000 on 2009-12-07
1gb would run Ubuntu alot better, but I dont think thats your problem. I have 512mb on my Ubuntu Box and It runs way better than when I run XP. It may be a graphics card issue. Are you running 9.10?

EDIT: Also, What Graphics Chipset are you using? If you cant find it Open Terminal **(Applications>Accessories>Terminal)** and type **lspci**. Then Post the Output here.

---

### Post by thedarthraider on 2009-12-08
Ok here it is.

mark@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

It does seem like it booted up quicker today.  Firefox is still running slow.

---

### Post by thedarthraider on 2009-12-09
Bump.

---

### Post by sweet_cogito on 2009-12-09
Firefox on linux based OSes is not really all that fast.  One benchmark I read a while back actually showed that firefox in wine ran faster than native firefox.  That coupled with the fact that your box isn't exactly a fast machine probably accounts for it.  If speed is your goal and you don't need much support for other stuff (like flash) try using something like links2.

---

### Post by joes7 on 2009-12-09
Are you multi-booting Ubuntu with another OS? If you are, try to compress files to make more space. Also, end useless processes to get some RAM back. 

Is your Ubuntu fully updated? Launch update manager and check. After updating it should work fine. If it doesnt, download Google Chrome or something.

Good Luck

---

