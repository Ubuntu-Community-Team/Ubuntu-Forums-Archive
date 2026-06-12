---
title: "Cant get desired resolution CRTC 0 FAILED"
date: 2010-05-15
forum: General Help
---

### Post by cadcam on 2010-05-15
so, I've been all over this website and the web trying to solve this issue.

I upgraded to lucid and switched monitors.  my new monitor is an acer x183h.  i'm trying to set it up in xrandr before i mess with any permanent files.  

i've done the following

                     pyramid@Pyramid:~$ cvt 1366 768  
 # 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz  
 Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync  
 pyramid@Pyramid:~$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync  
 pyramid@Pyramid:~$ xrandr  
 Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024  
 default connected 1280x1024+0+0 0mm x 0mm  
    1280x1024       0.0*  
    1024x768        0.0   
    800x600         0.0   
    640x480         0.0   
   1368x768_60.00 (0x11d)   85.0MHz  
         h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.6KHz  
         v: height  768 start  771 end  781 total  798           clock   59.7Hz
 
 
notice how it takes my 1366x768 and spits out 1368x768!

anyway. here is the rest

          pyramid@Pyramid:~$ xrandr --addmode default 1368x768_60.00  
 
          pyramid@Pyramid:~$ xrandr --output default --mode 1368x768_60.00  
 xrandr: screen cannot be larger than 1280x1024 (desired size 1368x768)  
 pyramid@Pyramid:~$ xrandr --output default --mode 1368x768_60.00  
 xrandr: Configure crtc 0 failed  
 pyramid@Pyramid:~$  
 
can someone please tell me what i am doing wrong....

this is a custom built computer with an asus server motherboard.  i'm using the computer as a server with a GUI.  everything about it is awesome except for this resolution busines.....

please help.

thank you,
A

---

### Post by cadcam on 2010-05-22
wow, i thought i would get more support than this in the ubuntu forums...

---

### Post by QLee on 2010-05-22
[QUOTE=cadcam]wow, i thought i would get more support than this in the ubuntu forums...[/QUOTE]

Yeah, perhaps it has something to do with how you described the monitor. You stated ASUS but you likely meant Acer.

On the other hand, I'm surprised that you didn't have any luck searching as, with a search engine, I easily found things about this old, cheap monitor, including posts about how its native resolution didn't work on windows either. Stuff about how the monitor didn't work with an nvidia riva too, but you didn't tell us anything about your hardware other than that typo of asus rather than acer.

If it was mine, I would try 1360 x 768 to see if I liked it better.

---

### Post by SlidingHorn on 2010-05-22
Could you please post the output from:

```
lspci
```

and your xorg.conf, if you have one?  That should help us get started

---

### Post by cadcam on 2010-05-24
Sure, sorry about the misnomer ealier, it is indeed an Acer, and I corrected that in the initial post.  

here is the hardware profile:

pyramid@Pyramid:~$ lspci
00:00.0 Host bridge: Intel Corporation 3200/3210 Chipset DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 3200/3210 Chipset Host-Primary PCI Express Bridge (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:01.0 RAID bus controller: Promise Technology, Inc. 20771 (FastTrak TX2300) (rev 02)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:03.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
pyramid@Pyramid:~$ 


Thanks for the input,
A

---

### Post by cadcam on 2010-05-24
regarding the xorg.conf .  there are a number of xorg.conf.####### files should i send the one with the biggest ###### or am I just missing the xorg.conf file?  i'm in the x11 folder.

thanks

---

### Post by cadcam on 2010-06-02
maybe ubuntu is incapable of supporting this resolution?  graphics hardware issue?  help?

---

### Post by cadcam on 2010-09-02
allight, in case anyone else out there has issues with similar hardware, use the SIS driver, and rewrite your xorg. conf.

i found out that xgi tech likes the sis driver, and they also provide source to their own driver from the website.

use this guys configs....

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9510678](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9510678)

---

