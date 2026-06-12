---
title: "ubuntu 11.04 &amp; 11.10 very laggy : kernel isue ?"
date: 2011-10-18
forum: General Help
---

### Post by Antoine3011 on 2011-10-18
Hello,

 Let me ask / beg for an ugly problem that has lasted long enough.
 I summarize the situation:

 On the disposal of 11.04, I did an update from my old system (I forget which version) and after a few seconds of normal activity, the system becames extremely slow. There was no crash, but opening the console took ten seconds, so you can not imagine what happens to open a web page ... I know a lot of problems with the graphics drivers are often observed, but this is not the case here. Indeed, these are all processes that are slow, my graphics drivers up to date. In addition, I eventually found a "solution" to boot on an older kernel that was available in the grub. MIRACLE ! It was not any more laggy.

 So I suspect the kernel.

 But now with the release of 11.10, I wanted to do a clean install and start again from scratch. And the problem is slow and reappeared. The 2 CPU are at 100% of activity for nothing ... The thing is I have the 3.0.0.12 generic entry (if I say no nonsense) available. So I want to know that you suggest as a solution to this problem.

 I tried to install the kernel 2.6.35-30.60, which is older (I do not know if it's a good idea) by searching synaptic "linux-image-2.6.35-30.60-generic" but I do not return anything.

 How to install a kernel just older? (simply because more manipulation I have to be done, more the system slowed down ...)
 Do you have any other suggestions?

 Thank you in advance for your help (which I think will serve to other people because I assumed not to be alone in this situation)

My config (obtained with windows):
[SIZE=1][COLOR=DimGray](.......)
       System Model: N51Vn               (ASUS)
               BIOS: Default System BIOS
          Processor: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz (2 CPUs), ~2.0GHz
             Memory: 4096MB RAM
Available OS Memory: 4096MB RAM
          Page File: 2467MB used, 5720MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7600.16385 32bit Unicode[/COLOR][/SIZE][SIZE=1][COLOR=DimGray]------------
DxDiag Notes
------------
      Display Tab 1: No problems found.
        Sound Tab 1: No problems found.
        Sound Tab 2: No problems found.
          Input Tab: No problems found.[/COLOR][/SIZE]
[SIZE=1][COLOR=DimGray]--------------------
DirectX Debug Levels
--------------------
Direct3D:    0/4 (retail)
DirectDraw:  0/4 (retail)
DirectInput: 0/5 (retail)
DirectMusic: 0/5 (retail)
DirectPlay:  0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow:  0/6 (retail)[/COLOR][/SIZE]
[SIZE=1][COLOR=DimGray]---------------
Display Devices
---------------
          Card name: NVIDIA GeForce GT 240M
       Manufacturer: NVIDIA
          Chip type: GeForce GT 240M
           DAC type: Integrated RAMDAC
         Device Key: Enum\PCI\VEN_10DE&DEV_0A34&SUBSYS_20341043&REV_A2
     Display Memory: 2778 MB
   Dedicated Memory: 986 MB
      Shared Memory: 1791 MB
       Current Mode: 1366 x 768 (32 bit) (60Hz)
       Monitor Name: Moniteur Plug-and-Play générique
      Monitor Model: unknown
         Monitor Id: CMO1571
        Native Mode: 1366 x 768(p) (60.046Hz)
        Output Type: Internal
        Driver Name: nvd3dumx.dll,nvwgf2umx.dll,nvwgf2umx.dll,nvd3dum,nvwgf2um,nvwgf2um
Driver File Version: 8.17.0012.6061 (English)
     Driver Version: 8.17.12.6061
        DDI Version: 10.1
       Driver Model: WDDM 1.1
  Driver Attributes: Final Retail
   Driver Date/Size: 9/10/2010 03:21:00, 12787304 bytes
        WHQL Logo'd: n/a
    WHQL Date Stamp: n/a
  Device Identifier: {D7B71E3E-4974-11CF-5E64-38001CC2C535}
          Vendor ID: 0x10DE
          Device ID: 0x0A34
          SubSys ID: 0x20341043
        Revision ID: 0x00A2
 Driver Strong Name: oem110.inf:NVIDIA_SetA_Devices.NTamd64.6.1:Section004:8.17.12.6061:pci\ven_10de&dev_0a34
     Rank Of Driver: 00E62001
        Video Accel: ModeMPEG2_A ModeMPEG2_C ModeVC1_C ModeWMV9_C 
   
(......)[/COLOR][/SIZE]


 PS: I had the same inssue in wanting to test fedora 15
 PS2: Sorry for my bag english

---

### Post by Antoine3011 on 2011-10-19
up ?

Actually I realy need some siggestions/helps cause I Can't do anything with such a slowness ... and I don't know how to downgrade a kernel easily.

Please ... :)

---

