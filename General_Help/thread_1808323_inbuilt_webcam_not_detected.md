---
title: "inbuilt webcam not detected"
date: 2011-07-20
forum: General Help
---

### Post by Gnomester on 2011-07-20
My Ubuntu 10.04 will not detect the inbuilt webcam on my Compaq Presario CQ61 laptop computer. This laptop only runs Ubuntu as I removed Windows when I got it home new from the shop a few years back. Haven't tried to get the webcam working until now. I have downloaded "Cheese" and when I run it I get the message No Device Found.I have also tried gstreamer-properties in a terminal and get the message video for linux 2 (v4l2): Cannot identify device '/dev/video0'

is it a lost cause to get my webcam working?

---

### Post by Quackers on 2011-07-20
Do you know what chipset the webcam is?
Have a look at the output of lspci or lsusb in the terminal and you should see it.

---

### Post by Gnomester on 2011-07-20
lspci gives me.....

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

lsusb gives me....

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

would I be better off buying a webcam that is known to be supported by the Lucid Lynx

---

### Post by Quackers on 2011-07-20
Hmm, strange. What laptop is it?

---

### Post by Gnomester on 2011-07-20
Compaq Presario CQ61

---

### Post by Quackers on 2011-07-20
There are many CQ61 versions, it seems. Have a look at the sticker on the bottom. It should give you a specific model number.
It also appears that there is a switch for the webcam, or it could be a Fn + key combination. Have you tried that? Have a look in the manual for details.

---

### Post by nomko on 2011-07-20
[COLOR=red]deleted[/COLOR]

---

### Post by Quackers on 2011-07-20
Have you seen post #3? :-)

---

### Post by no2498 on 2011-07-20
put this in a terminal dmesg click enter

in your package manager look for and install xawtv
try the cam in xawtv first not cheese

---

### Post by nomko on 2011-07-21
> **Quackers said:**
> Have you seen post #3? :-)
 
Yeah, i did, later. I had the reply window open for a long time and send it. After that i saw it.

---

### Post by Gnomester on 2011-07-27
I believe that the Fn + F4 key combination toggles the webcam on my laptop

lspci and lsusb return the same results before and after using the above key combination.

when running cheese the program blinks when I toggle the key combination but still returns the error message that the webcam is not found.

xawtv won't run at all

I have made sure that I have user privileges set to allow access to video

I feel that the cam is not being recognised by the system at all should I be able to find /dev/video0 somewhere in the system? as gstreamer properties lists...

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src1:
system error: No such file or directory

the multimedia systems selection window default output is blank for both the device and pipeline

---

### Post by no2498 on 2011-07-27
xawtv loaded a cam grabber so thats good
do the fn f4 keys before you open cheese
put this in a terminal 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by Gnomester on 2011-07-27
> **no2498 said:**
> xawtv loaded a cam grabber so thats good
do the fn f4 keys before you open cheese
put this in a terminal 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

I have done the fn f4 combo before I opened cheese

If xawtv loaded a cam grabber, where can I see this? when I run this program nothing happens.

I struggle to get sound to work with this OS, why is it so hard to get video to work as well!!
I am suffering years of ubuntu frustration and I want a fix now!!!

---

### Post by no2498 on 2011-07-27
in a terminal type dmesg click enter
look around the bottom did it find the cam

---

### Post by Gnomester on 2011-08-13
I have given up on the inbuilt cam and I have borrowed a USB Microsoft lifecam which does work in Cheese. Still having problems with Adobe Flash recognising the cam in Firefox but it works OK in Opera? I have since found that Firefox does recognise the inbuilt microphone when trying to use flash but not the mic on the camera as well as the video. Tried all the flash player preferences in Ubuntu and at Adobe without any luck with Firefox. I have updated to Ubuntu 10.10 with Firefox 3.16.18.
Have also tried to run Flash-aid and it won't work as when I run the wizard I end up with an error message.....There was an error creating the child process for this terminal getpt failed: No such file or directory.

don't know what to do next as I would prefer to use Firefox as my main web browser

---

### Post by no2498 on 2011-08-13
every thing you need for fire fox should be here

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

