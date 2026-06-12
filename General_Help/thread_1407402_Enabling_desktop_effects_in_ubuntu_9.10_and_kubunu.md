---
title: "Enabling desktop effects in ubuntu 9.10 and kubunut 9.10 ATI Radeon 9550"
date: 2010-02-15
forum: General Help
---

### Post by sluwtje on 2010-02-15
With the Ati Radeon 9550, desktop effects can be enabled in ubuntu 9.10 and kubuntu 9.10 here is how:

In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.
 Now execute the following commands:
 user@ubuntu ~# sudo service gdm stop
 This command will stop the X.
 Now we need to generate the xorg.conf file:
 user@ubuntu ~# sudo Xorg -configure
 This has generated the file in ~/xorg.conf.new.
 We need to make the X using it so we have to put this file inside /etc/X11/
 user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
 After moving this file to the proper location you can start the X again and see what happens:
 user@ubuntu ~# sudo service gdm start


_For KDE gdm has to be replaced with kdm_


Then follow the instructions on this page for ubuntu: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

 
For KDE, the instructions are a little bit different, follow the tutorial above until you get to the....
**Configuring your graphics card "Device" section**

then you add only this option in the "device" section.
Option          "XAANoOffscreenPixmaps"

and enable or add this in the "device" section.

Option        "BusType" "PCI"
Option        "AGPMode" "1"
        Option         "AGPMode" "1"
 Then Add the following sections at the end of the file if they don't exist elsewhere:

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection 

Then do CTRL + ALT + F1.
 Now execute the following commands:
 user@ubuntu ~# sudo service kdm stop
 This command will stop KDE


Then do CTRL + ALT + F7 or ALT+F7

  Now execute the following commands:
  user@ubuntu ~# sudo service kdm start
  This command will start KDE


Login as normal


Open Konsole
and do type.


$ glxinfo | grep vendor
When al is good it should say SGI

$ glxinfo | grep "direct rendering"
If you get *No direct rendering*, then your card probably is not supported by the open source driver. You will have to install the [proprietary fglrx driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). 

Else all is fine, you can restart and enable desktop effects, if its not enabled yet.

It worked for me.

I added my xorg.conf as a sample, its in the .zip file

---

### Post by ssparti on 2010-02-18
I've tried following a few of these tutorials and I still can't get my graphics card to work.

Here is my lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68be
01:00.1 Audio device: ATI Technologies Inc Device aa58
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

I have a Radeon ATI 5750 graphics card and I think I have everything configured correctly.

steve@steve-desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project
steve@steve-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

But when I try to enable "visual effects" it doesn't work.  Any Ideas?  I'm new to Ubuntu so a walkthrough would really help me.  Thanks.

---

### Post by leftfinger on 2010-02-18
Thanks to sluwtje, your config works though not perfect.
I've tested it and found the key point is to force use PCI mode for AGP card (Radeon 9550 is a AGP card). Others seem not affect much.
And another thing I found is, system becomes unstable (at least compares to the one before mod). I encountered system hanging many times. And even the REISUB sequence doesn't respond at that moment.

Finally, on the way of continuing testing the solution sluwtje posted, I decided to do the search again, to see whether there's a perfect solution yet. And, yes, I think now we have it.
The cause we cannot enable visual effects comes from lack of driver support. Driver embedded in current kernel in use doesn't support ATI card that well. But, now there's good news. Since ATI opened some code days ago, we now are able to use kernels which have better driver code embedded in.

I've tested the kernel of version 2.6.32.8 (although it's better to wait for ubuntu team releasing the new ones into software channel 'cause that'll be with better integration to system but I just can't wait) and it works like a charm. Thanks to ATI and thanks to kernel team, you're great!

Hi, ssparti, the prb can be tell from this line from your post:
[INDENT]OpenGL vendor string: Mesa Project[/INDENT]
For a good one, it should be like:
[INDENT]OpenGL vendor string: DRI R300 Project[/INDENT]

And you can judge it by "glxinfo |grep -i opengl". For a good one, the result should be like:
[INDENT]OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV350 4153) 20090101 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.5 Mesa 7.6
OpenGL extensions:[/INDENT]
Note the second line, means have identified the graphic card correctly and driver for it is ok.

I recommend you wait for the official release of kernel updates if you can. 'Cause that will be more stable. For me, I just can't wait.:D

And, finally, thanks to you guys for the info!:popcorn:

---

