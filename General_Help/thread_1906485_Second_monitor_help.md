---
title: "Second monitor help"
date: 2012-01-09
forum: General Help
---

### Post by woopud on 2012-01-09
I just installed Lubuntu on my Dell Dimension 8300, I also have two Dell LCD monitors, booted up from the LiveCD and both monitors worked but after installation onle one of them works.  if I go into NVIDIA X server settings it also shows one monitor, I've had Ubuntu before with the dual screen setup (extended desktop).  Any help is appreciated.

---

### Post by David Crockett on 2012-01-09
Hi,

I have the same problem with my computer.    I have not been able to solve it.  You will have to post more information for the community to help including  /etc/X11/xorg.conf

In my case my  /etc/X11/xorg.conf seems to have been replaced by the following rather simple one:

Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


I don't know how to revise this.   I have done the third party driver download thing and the NVIVIA X server settings program does not seem to know how to reconfigure my Xorg.conf file.    And I do not know how to get it to do so or really how to do it manually.    I have tried to do so and made a mess and ended up reinstalling Ubuntu.  

The strange thing is that the system recognizes the the two monitors when I start up and shut down.     

I would also suggest posting the results of the lspci  command.   Mine gives the following results.

crockett@cuneatus-1-0:~$ sudo lspci
[sudo] password for crockett: 
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev a2)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)

I am at a loss as to what to do.    If you don't get it right it can be a real disaster.

Regards,
David

---

### Post by David Crockett on 2012-01-09
BTW

Both of my monitors work just fine when running Ubuntu from the CD.    And both monitors are recognized and are working during boot up until the desktop logon screen apprears At which time it only appears on one screen.  During shutdown, both screens are active.

Cheers,
DC

---

### Post by SteveDee on 2012-01-11
Open terminal and type:-
```

xrandr

```
...and post your output.

---

### Post by woopud on 2012-06-29
I still haven't figured the dual screen setup yet, can anyone help me?  I had it working a while ago but had to reinstall Ubuntu and now I can't figure out how I did it last time.

woopud@Woopud-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)
02:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:03.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
woopud@Woopud-PC:~$ 


woopud@Woopud-PC:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0     51.0* 
   1280x960       52.0  
   1152x864       53.0     54.0     55.0     56.0  
   1024x768       57.0     58.0     59.0  
   960x600        60.0  
   960x540        61.0  
   840x525        62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0  
   800x512        72.0  
   720x450        73.0  
   680x384        74.0     75.0  
   640x512        76.0     77.0  
   640x480        78.0     79.0     80.0     81.0     82.0  
   576x432        83.0     84.0     85.0     86.0  
   512x384        87.0     88.0     89.0  
   416x312        90.0  
   400x300        91.0     92.0     93.0     94.0  
   320x240        95.0     96.0     97.0  
woopud@Woopud-PC:~$

---

