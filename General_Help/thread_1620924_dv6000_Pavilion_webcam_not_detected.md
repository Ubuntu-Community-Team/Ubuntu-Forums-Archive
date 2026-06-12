---
title: "dv6000 Pavilion webcam not detected"
date: 2010-11-13
forum: General Help
---

### Post by tango_ninja on 2010-11-13
Not sure exactly where to go on this one...  I'm trying to get the embedded/stock webcam on my wife's Dell dv6000 to work.  I'm pretty sure Ubuntu can't see it all right now.  

I'm told that this webcam works fine via uvcvideo and have tried to install the package but am thinking the problem is with ubuntu's detection itself.

Hopefully someone with more experience than I can point me in the right direction...

**_Outputs:_**
```
christina@christina-laptop:~$** ls -la /dev/v***
crw-rw---- 1 root tty   7,   0 2010-11-13 15:26 /dev/vcs
crw-rw---- 1 root tty   7,   1 2010-11-13 15:26 /dev/vcs1
crw-rw---- 1 root tty   7,   2 2010-11-13 15:26 /dev/vcs2
crw-rw---- 1 root tty   7,   3 2010-11-13 15:26 /dev/vcs3
crw-rw---- 1 root tty   7,   4 2010-11-13 15:26 /dev/vcs4
crw-rw---- 1 root tty   7,   5 2010-11-13 15:26 /dev/vcs5
crw-rw---- 1 root tty   7,   6 2010-11-13 15:26 /dev/vcs6
crw-rw---- 1 root tty   7,   7 2010-11-13 15:26 /dev/vcs7
crw-rw---- 1 root tty   7, 128 2010-11-13 15:26 /dev/vcsa
crw-rw---- 1 root tty   7, 129 2010-11-13 15:26 /dev/vcsa1
crw-rw---- 1 root tty   7, 130 2010-11-13 15:26 /dev/vcsa2
crw-rw---- 1 root tty   7, 131 2010-11-13 15:26 /dev/vcsa3
crw-rw---- 1 root tty   7, 132 2010-11-13 15:26 /dev/vcsa4
crw-rw---- 1 root tty   7, 133 2010-11-13 15:26 /dev/vcsa5
crw-rw---- 1 root tty   7, 134 2010-11-13 15:26 /dev/vcsa6
crw-rw---- 1 root tty   7, 135 2010-11-13 15:26 /dev/vcsa7
crw-rw---- 1 root root 10,  63 2010-11-13 15:26 /dev/vga_arbiter
```

```
christina@christina-laptop:~$** gstreamer-properties**
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': [COLOR="red"]Device "/dev/video0" does not exist.[/COLOR] [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': [COLOR="Red"]Cannot identify device '/dev/video0'[/COLOR]. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]
```

```
christina@christina-laptop:~$** camorama -D**
VIDIOCGCAP  --  could not get camera capabilities, exiting.....
[COLOR="red"][Gui says: Could not connect to video device /dev/video0.  Please check connection[/COLOR]]
```

And I get a "No device found" upon launching Cheese.

Any takers?

Thanks a bunch

---

### Post by tango_ninja on 2010-11-14
Update: was using kernel 2.6.32-35-generic and thought perhaps updating to a newer kernel might help.

Updated to 2.6.35.8 from [http://kernel.org/](http://kernel.org/) but no luck...same problem.

---

### Post by no2498 on 2010-11-15
look for the program called cheese webcam booth in sound&video for it
if not installed
open a terminal type sudo apt-get install cheese

i hope it comes on in cheese

in a terminal type lsusb click enter
should tell you the cam name& #
to see if you need a driver for it

but most webcams just work now days

---

### Post by Ric_NYC on 2010-11-15
Today: "no device found"


Cheese cannot detect the webcam. 

Acer Aspire 5515.


Any help is appreciated.

Thanks.

---

### Post by tango_ninja on 2010-11-20
> **no2498 said:**
> look for the program called cheese webcam booth in sound&video for it
if not installed
open a terminal type sudo apt-get install cheese

i hope it comes on in cheese

in a terminal type lsusb click enter
should tell you the cam name& #
to see if you need a driver for it

but most webcams just work now days

Hi -- thanks, yes I have Cheese, it doesn't work.  It gives me "No device found" upon launch.

```
christina@christina-laptop:~$ **lsusb**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Not sure where to go with this info... I'm not 100% sure if this applies since this is an HP Pavilion webcam built-in to the laptop.  Not connected via external usb.

---

### Post by no2498 on 2010-11-22
do you need to push a key like fn to turn the cam on
ive never had a laptop

but the cam should show in lsusb if the cam is on

---

### Post by tango_ninja on 2010-11-27
nope, camera doesn't have an on button and works fine in windows

---

### Post by Quackers on 2010-11-27
Try lspci please. It may be a pci device.

---

### Post by tango_ninja on 2010-11-27
ok here it is.  nothing is standing out to my eyes

```
christina@christina-laptop:~$ **lspci**
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

---

### Post by Quackers on 2010-11-27
No, I don't see anything either. 
My camera did this and I found out what the chipset was through Windows (Ricoh r5U87x).
Do you still have Windows on there? See what the device is called in the device manager and we can go from there.
Or maybe run Everest free version to find out.

---

### Post by tango_ninja on 2011-01-08
rats, nope... no more windows.  I'll keep searching for drivers I suppose.

---

### Post by no2498 on 2011-01-09
on lap tops you do need to push keys like fn+f2 or f4 to turn the cam on
as a cam would run the battery down
the cam program should turn it off 

fn+ f2 or f4 keys at the same time

then run in  the terminal lsusb

---

### Post by tango_ninja on 2011-01-09
> **no2498 said:**
> on lap tops you do need to push keys like fn+f2 or f4 to turn the cam on
as a cam would run the battery down
the cam program should turn it off 

fn+ f2 or f4 keys at the same time

then run in  the terminal lsusb

Yeah that's a good idea, but this laptop doesn't use any function keys to power on or off the webcam...  lsusb still doesn't show any video

---

### Post by no2498 on 2011-01-11
do you ever see the cam light come on ?
you need to go ask the computer maker how to turn the cam on

---

### Post by polrus on 2012-08-07
has anyone else solved this problem?
the strange thing is that the webcam used to work for me for some time and suddenly it's not detected anymora by lsusb
maybe there's a hidden swith - or software trigger needed?

---

### Post by oldos2er on 2012-08-07
Old thread closed; please start a new thread.

---

