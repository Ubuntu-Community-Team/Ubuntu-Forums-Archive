---
title: "how to get syntek webcam to work?"
date: 2010-05-27
forum: General Help
---

### Post by MasterShihoChief on 2010-05-27
I have tried to get my webcam to work, i know its a syntek as i checked the windows driver ini file that came with my computer and it shows a internal syntek webcam with mic, but cheese just a color bar screen or just black or just static.

i tried installing the syntek driver i found online for ubuntu and it didnt work. any help would be great.

```
mastershihochief@cortanamobile:~/Downloads$ cd stk*
mastershihochief@cortanamobile:~/Downloads/stk11xx-2.1.0$ make -f Makefile.standalone
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/mastershihochief/Downloads/stk11xx-2.1.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.o
/home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.c:1737: error: unknown field ‘compat_ioctl’ specified in initializer
/home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.c:1737: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
make[2]: *** [/home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.o] Error 1
make[1]: *** [_module_/home/mastershihochief/Downloads/stk11xx-2.1.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [driver] Error 2
mastershihochief@cortanamobile:~/Downloads/stk11xx-2.1.0$ 

```

---

### Post by no2498 on 2010-05-27
this may help

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

hope it come on

910 and up cheese webcam booth should be loaded
look in sound & video
try the cam in cheese
most webcams should work and not need a diff driver

hope this helps

---

### Post by MasterShihoChief on 2010-05-28
```
mastershihochief@cortanamobile:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]
  


```

---

### Post by MasterShihoChief on 2010-05-28
So it seems the problem is the Syntek driver never installed. I go the following errors after i tried to recompile the driver after making clean. I don't know why I get this error, I have the header files installed in that directory and i double checked, and it is there.

```
mastershihochief@cortanamobile:~/Downloads/stk11xx-2.1.0$ sudo make -f Makefile.standalone clean
[sudo] password for mastershihochief: 
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS= clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CLEAN   /usr/src/linux-headers-2.6.32-22-generic
/usr/src/linux-headers-2.6.32-22-generic/drivers/staging/rt3090/Makefile:3: drivers/staging/rt3090/config.mk: No such file or directory
make[4]: *** No rule to make target `drivers/staging/rt3090/config.mk'.  Stop.
make[3]: *** [drivers/staging/rt3090] Error 2
make[2]: *** [drivers/staging] Error 2
make[1]: *** [_clean_drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [clean] Error 2
mastershihochief@cortanamobile:~/Downloads/stk11xx-2.1.0$ sudo make -f Makefile.standalone
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [driver] Error 2
mastershihochief@cortanamobile:~/Downloads/stk11xx-2.1.0$ 

```

---

### Post by no2498 on 2010-05-28
make[2]: *** No rule to make target

? did you leave out a step 
i am NOT a coder but looks like you need to make install

---

### Post by MasterShihoChief on 2010-05-28
how do i make an install on a linux header? i thought the whole purpose of having the linux header installed was so u didnt have to compile the whole kernel and everything when u wanted to build a module for driver, or am i wrong?

---

### Post by MasterShihoChief on 2010-05-30
bump plz

---

### Post by no2498 on 2010-05-31
sudo apt-get install ubuntu-restricted-extras



you do that yet

---

### Post by MasterShihoChief on 2010-06-01
ya already did that day one of install.

---

### Post by no2498 on 2010-06-02
start a new ? 

im not able to help you 

sorry

---

### Post by MasterShihoChief on 2010-06-03
np thx for your help, someone else maybe? bump.

---

### Post by MasterShihoChief on 2010-06-04
bump

---

### Post by no2498 on 2010-06-06
did you try the cam in cheese webcam booth ?

---

### Post by MasterShihoChief on 2010-06-06
ya its all black, no picture, and then there the error that says video0 doesnt exist or something

---

### Post by no2498 on 2010-06-07
in a terminal type cheese -v

what does it say

---

### Post by MasterShihoChief on 2010-06-08
mastershihochief@cortanamobile:~$ cheese -v
Cheese 2.30.1 
libv4l2: error setting pixformat: Input/output error
Segmentation fault
mastershihochief@cortanamobile:~$

---

### Post by no2498 on 2010-06-08
you did do this yes ?

sudo apt-get install ubuntu-restricted-extras


or try this before you start cheese -v

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese


is a lib4l
something like libv4l/v4l1compat.so that we need i have only seen 1 time was in synaptic but cant remember it sorry

---

### Post by MasterShihoChief on 2010-06-08
libv4l-0 is installed. the dev package isnt, but the main one is. As for the restricted extras i did that a long time ago so i could play my music and watch videos which work fine. I ran it again anyways just to make sure and it said nothing changed, its up to date.

---

### Post by MasterShihoChief on 2010-06-12
someone have any ideas bump?

---

### Post by pyrocloud on 2010-06-12
You are likely trying to load a 32 bit driver onto a 64 bit OS. 

You will need to find a 64 bit driver for your webcam. If you find one please post back here, as this thread is pretty high on Google for syntek webcam driver ubuntu. 

Cheers

---

### Post by MasterShihoChief on 2010-06-25
Ive been trying using the following driver.

[http://syntekdriver.sourceforge.net/]("http://syntekdriver.sourceforge.net/")

Dont know if its the 64 bit driver like u said, but it is still in development which is probably why it doesnt work properly.

---

### Post by okplayer02 on 2010-06-26
first plug in the webcam and from command line type the command 

```
lsusb
```then post the results this lists all the usb devices plugged in to your pc 

also type from the command line

```
dmesg
```this prints out kernel messages we will see if the firmware for that camera is in the kernel and if the module is loaded

---

### Post by MasterShihoChief on 2010-06-26
lsusb results


mastershihochief@cortanamobile:~$ lsusb
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 187c:0511  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 047: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 002 Device 046: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 002 Device 045: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 002 Device 044: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 043: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 174f:8a51 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mastershihochief@cortanamobile:~$ 
```

please keep in mind this is not an external webcam connected by usb, this is an internal laptop webcam. 

dmesg results(a bunch got cut off):


```
[321063.092214] generic-usb 0003:046D:C01E.008F: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[321063.450248] usb 2-4.1: USB disconnect, address 121
[321063.742918] usb 2-4.1: new low speed USB device using ehci_hcd and address 122
[321063.855523] usb 2-4.1: configuration #1 chosen from 1 choice
[321063.859862] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input152
[321063.859997] generic-usb 0003:046D:C01E.0090: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[321064.216752] usb 2-4.1: USB disconnect, address 122
[321064.502894] usb 2-4.1: new low speed USB device using ehci_hcd and address 123
[321064.617930] usb 2-4.1: configuration #1 chosen from 1 choice
[321064.621743] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input153
[321064.621870] generic-usb 0003:046D:C01E.0091: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[321064.984630] usb 2-4.1: USB disconnect, address 123
[321065.272772] usb 2-4.1: new low speed USB device using ehci_hcd and address 124
[321065.388149] usb 2-4.1: configuration #1 chosen from 1 choice
[321065.392929] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input154
[321065.393050] generic-usb 0003:046D:C01E.0092: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322007.064898] usb 2-4.1: USB disconnect, address 124
[322007.352905] usb 2-4.1: new low speed USB device using ehci_hcd and address 125
[322007.467932] usb 2-4.1: configuration #1 chosen from 1 choice
[322007.473567] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input155
[322007.473714] generic-usb 0003:046D:C01E.0093: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322007.577277] usb 2-4.1: USB disconnect, address 125
[322007.930386] usb 2-4.1: new low speed USB device using ehci_hcd and address 126
[322008.045705] usb 2-4.1: configuration #1 chosen from 1 choice
[322008.049734] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input156
[322008.049858] generic-usb 0003:046D:C01E.0094: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322008.344875] usb 2-4.1: USB disconnect, address 126
[322008.633516] usb 2-4.1: new low speed USB device using ehci_hcd and address 127
[322008.748047] usb 2-4.1: configuration #1 chosen from 1 choice
[322008.752145] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input157
[322008.752267] generic-usb 0003:046D:C01E.0095: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322009.112966] usb 2-4.1: USB disconnect, address 127
[322009.432894] usb 2-4.1: new low speed USB device using ehci_hcd and address 2
[322009.548321] usb 2-4.1: configuration #1 chosen from 1 choice
[322009.551993] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input158
[322009.552117] generic-usb 0003:046D:C01E.0096: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322009.624876] usb 2-4.1: USB disconnect, address 2
[322009.912766] usb 2-4.1: new low speed USB device using ehci_hcd and address 5
[322010.028042] usb 2-4.1: configuration #1 chosen from 1 choice
[322010.032104] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input159
[322010.032231] generic-usb 0003:046D:C01E.0097: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322010.136872] usb 2-4.1: USB disconnect, address 5
[322010.452762] usb 2-4.1: new low speed USB device using ehci_hcd and address 8
[322010.572741] usb 2-4.1: configuration #1 chosen from 1 choice
[322010.576469] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input160
[322010.576635] generic-usb 0003:046D:C01E.0098: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322010.648866] usb 2-4.1: USB disconnect, address 8
[322010.942801] usb 2-4.1: new low speed USB device using ehci_hcd and address 9
[322011.058415] usb 2-4.1: configuration #1 chosen from 1 choice
[322011.061900] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input161
[322011.062039] generic-usb 0003:046D:C01E.0099: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322011.160997] usb 2-4.1: USB disconnect, address 9
[322011.446151] usb 2-4.1: new low speed USB device using ehci_hcd and address 10
[322011.557901] usb 2-4.1: configuration #1 chosen from 1 choice
[322011.561866] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input162
[322011.562001] generic-usb 0003:046D:C01E.009A: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322011.672756] usb 2-4.1: USB disconnect, address 10
[322011.972901] usb 2-4.1: new low speed USB device using ehci_hcd and address 11
[322012.088038] usb 2-4.1: configuration #1 chosen from 1 choice
[322012.091984] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input163
[322012.092122] generic-usb 0003:046D:C01E.009B: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322012.184883] usb 2-4.1: USB disconnect, address 11
[322012.492763] usb 2-4.1: new low speed USB device using ehci_hcd and address 13
[322012.607879] usb 2-4.1: configuration #1 chosen from 1 choice
[322012.612099] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input164
[322012.612223] generic-usb 0003:046D:C01E.009C: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322362.392796] usb 2-4.1: USB disconnect, address 13
[322362.681955] usb 2-4.1: new low speed USB device using ehci_hcd and address 14
[322362.795342] usb 2-4.1: configuration #1 chosen from 1 choice
[322362.799669] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input165
[322362.799794] generic-usb 0003:046D:C01E.009D: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322364.184943] usb 2-4.1: USB disconnect, address 14
[322364.501037] usb 2-4.1: new low speed USB device using ehci_hcd and address 15
[322364.615506] usb 2-4.1: configuration #1 chosen from 1 choice
[322364.620084] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input166
[322364.620215] generic-usb 0003:046D:C01E.009E: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322365.208799] usb 2-4.1: USB disconnect, address 15
[322365.502965] usb 2-4.1: new low speed USB device using ehci_hcd and address 16
[322365.618106] usb 2-4.1: configuration #1 chosen from 1 choice
[322365.623198] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input167
[322365.623323] generic-usb 0003:046D:C01E.009F: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322366.233070] usb 2-4.1: USB disconnect, address 16
[322366.530331] usb 2-4.1: new low speed USB device using ehci_hcd and address 17
[322366.647922] usb 2-4.1: configuration #1 chosen from 1 choice
[322366.652159] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input168
[322366.652286] generic-usb 0003:046D:C01E.00A0: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322368.024944] usb 2-4.1: USB disconnect, address 17
[322368.331958] usb 2-4.1: new low speed USB device using ehci_hcd and address 18
[322368.448095] usb 2-4.1: configuration #1 chosen from 1 choice
[322368.452367] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input169
[322368.452491] generic-usb 0003:046D:C01E.00A1: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[322469.342614] UDP: short packet: From 0.0.0.0:0 0/151 to 0.0.0.0:0
[324164.377299] usb 2-4.1: USB disconnect, address 18
[324164.672933] usb 2-4.1: new low speed USB device using ehci_hcd and address 19
[324164.787991] usb 2-4.1: configuration #1 chosen from 1 choice
[324164.791875] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input170
[324164.791994] generic-usb 0003:046D:C01E.00A2: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[324167.193070] usb 2-4.1: USB disconnect, address 19
[324167.492791] usb 2-4.1: new low speed USB device using ehci_hcd and address 20
[324167.607914] usb 2-4.1: configuration #1 chosen from 1 choice
[324167.612409] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input171
[324167.612584] generic-usb 0003:046D:C01E.00A3: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[324168.985016] usb 2-4.1: USB disconnect, address 20
[324169.282918] usb 2-4.1: new low speed USB device using ehci_hcd and address 21
[324169.397940] usb 2-4.1: configuration #1 chosen from 1 choice
[324169.403039] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input172
[324169.403186] generic-usb 0003:046D:C01E.00A4: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[326895.299126] UDP: short packet: From 0.0.0.0:56329 0/151 to 0.0.0.0:0
[329542.771766] chrome[17169]: segfault at bbadbeef ip 0000000001217df8 sp 00007fffef79c300 error 6 in chrome[400000+2a14000]
[331372.570103] usb 2-4.1: USB disconnect, address 21
[331372.872832] usb 2-4.1: new low speed USB device using ehci_hcd and address 22
[331372.985466] usb 2-4.1: configuration #1 chosen from 1 choice
[331372.989499] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input173
[331372.989626] generic-usb 0003:046D:C01E.00A5: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[331376.665953] usb 2-4.1: USB disconnect, address 22
[331376.980334] usb 2-4.1: new low speed USB device using ehci_hcd and address 23
[331377.095474] usb 2-4.1: configuration #1 chosen from 1 choice
[331377.099465] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input174
[331377.099597] generic-usb 0003:046D:C01E.00A6: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[333164.059818] usb 2-4.1: USB disconnect, address 23
[333164.390325] usb 2-4.1: new low speed USB device using ehci_hcd and address 24
[333164.505436] usb 2-4.1: configuration #1 chosen from 1 choice
[333164.509550] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input175
[333164.509677] generic-usb 0003:046D:C01E.00A7: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[333174.554566] usb 2-4.1: USB disconnect, address 24
[333174.872824] usb 2-4.1: new low speed USB device using ehci_hcd and address 25
[333174.985714] usb 2-4.1: configuration #1 chosen from 1 choice
[333174.990153] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input176
[333174.990274] generic-usb 0003:046D:C01E.00A8: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[333175.834299] usb 2-4.1: USB disconnect, address 25
[333176.140330] usb 2-4.1: new low speed USB device using ehci_hcd and address 26
[333176.255666] usb 2-4.1: configuration #1 chosen from 1 choice
[333176.260774] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input177
[333176.260904] generic-usb 0003:046D:C01E.00A9: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[333177.626184] usb 2-4.1: USB disconnect, address 26
[333177.942461] usb 2-4.1: new low speed USB device using ehci_hcd and address 27
[333178.055820] usb 2-4.1: configuration #1 chosen from 1 choice
[333178.060358] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input178
[333178.060480] generic-usb 0003:046D:C01E.00AA: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[333189.402316] usb 2-4.1: USB disconnect, address 27
[333189.700324] usb 2-4.1: new low speed USB device using ehci_hcd and address 28
[333189.815561] usb 2-4.1: configuration #1 chosen from 1 choice
[333189.820148] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input179
[333189.820302] generic-usb 0003:046D:C01E.00AB: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[333311.770207] usb 2-4.1: USB disconnect, address 28
[333312.060345] usb 2-4.1: new low speed USB device using ehci_hcd and address 29
[333312.177927] usb 2-4.1: configuration #1 chosen from 1 choice
[333312.182382] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input180
[333312.182544] generic-usb 0003:046D:C01E.00AC: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335694.106761] usb 2-4.1: USB disconnect, address 29
[335694.420387] usb 2-4.1: new low speed USB device using ehci_hcd and address 30
[335694.535387] usb 2-4.1: configuration #1 chosen from 1 choice
[335694.539169] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input181
[335694.539279] generic-usb 0003:046D:C01E.00AD: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335696.154490] usb 2-4.1: USB disconnect, address 30
[335696.450385] usb 2-4.1: new low speed USB device using ehci_hcd and address 31
[335696.565397] usb 2-4.1: configuration #1 chosen from 1 choice
[335696.569218] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input182
[335696.569336] generic-usb 0003:046D:C01E.00AE: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335696.666620] usb 2-4.1: USB disconnect, address 31
[335696.970250] usb 2-4.1: new low speed USB device using ehci_hcd and address 32
[335697.075648] usb 2-4.1: configuration #1 chosen from 1 choice
[335697.082480] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input183
[335697.082609] generic-usb 0003:046D:C01E.00AF: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335697.690521] usb 2-4.1: USB disconnect, address 32
[335697.990386] usb 2-4.1: new low speed USB device using ehci_hcd and address 33
[335698.105388] usb 2-4.1: configuration #1 chosen from 1 choice
[335698.109921] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input184
[335698.110045] generic-usb 0003:046D:C01E.00B0: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335698.202474] usb 2-4.1: USB disconnect, address 33
[335698.482893] usb 2-4.1: new low speed USB device using ehci_hcd and address 34
[335698.595651] usb 2-4.1: configuration #1 chosen from 1 choice
[335698.600987] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input185
[335698.601119] generic-usb 0003:046D:C01E.00B1: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335698.714747] usb 2-4.1: USB disconnect, address 34
[335699.012745] usb 2-4.1: new low speed USB device using ehci_hcd and address 35
[335699.125392] usb 2-4.1: configuration #1 chosen from 1 choice
[335699.130081] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input186
[335699.130206] generic-usb 0003:046D:C01E.00B2: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335699.482615] usb 2-4.1: USB disconnect, address 35
[335699.790260] usb 2-4.1: new low speed USB device using ehci_hcd and address 36
[335699.905441] usb 2-4.1: configuration #1 chosen from 1 choice
[335699.909596] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input187
[335699.909719] generic-usb 0003:046D:C01E.00B3: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335699.994628] usb 2-4.1: USB disconnect, address 36
[335700.292891] usb 2-4.1: new low speed USB device using ehci_hcd and address 37
[335700.406392] usb 2-4.1: configuration #1 chosen from 1 choice
[335700.410499] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input188
[335700.410623] generic-usb 0003:046D:C01E.00B4: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[335956.261682] UDP: short packet: From 0.0.0.0:0 0/151 to 0.0.0.0:0
[336841.293021] npviewer.bin[24567]: segfault at e8358071 ip 00000000e8358071 sp 00000000e8358071 error 14
[339037.979052] usb 2-4.1: USB disconnect, address 37
[339038.262179] usb 2-4.1: new low speed USB device using ehci_hcd and address 38
[339038.375451] usb 2-4.1: configuration #1 chosen from 1 choice
[339038.379468] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input189
[339038.379580] generic-usb 0003:046D:C01E.00B5: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[339046.682940] usb 2-4.1: USB disconnect, address 38
[339046.980311] usb 2-4.1: new low speed USB device using ehci_hcd and address 39
[339051.029195] hub 2-4:1.0: hub_port_status failed (err = -71)
[339051.033313] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.037438] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.043064] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.047064] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.047068] hub 2-4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[339051.051181] hub 2-4:1.0: cannot disable port 1 (err = -71)
[339051.055292] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.059420] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.063543] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.067665] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.071805] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.071809] hub 2-4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[339051.075939] hub 2-4:1.0: cannot disable port 1 (err = -71)
[339051.080164] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.084253] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.088309] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.092424] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.096557] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.096559] hub 2-4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[339051.100679] hub 2-4:1.0: cannot disable port 1 (err = -71)
[339051.104807] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.108928] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.113049] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.117195] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.121301] hub 2-4:1.0: cannot reset port 1 (err = -71)
[339051.121304] hub 2-4:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[339051.125433] hub 2-4:1.0: cannot disable port 1 (err = -71)
[339051.125438] hub 2-4:1.0: unable to enumerate USB device on port 1
[339051.129552] hub 2-4:1.0: cannot disable port 1 (err = -71)
[339051.133678] hub 2-4:1.0: hub_port_status failed (err = -71)
[339051.133691] usb 2-4: USB disconnect, address 4
[339051.133693] usb 2-4.2: USB disconnect, address 6
[339051.211351] usb 2-4.3: USB disconnect, address 7
[339051.284480] usb 2-4.4: USB disconnect, address 12
[339053.060113] usb 2-4: new high speed USB device using ehci_hcd and address 43
[339053.211560] usb 2-4: configuration #1 chosen from 1 choice
[339053.212054] hub 2-4:1.0: USB hub found
[339053.212430] hub 2-4:1.0: 4 ports detected
[339053.490313] usb 2-4.1: new low speed USB device using ehci_hcd and address 44
[339053.605541] usb 2-4.1: configuration #1 chosen from 1 choice
[339053.609418] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input190
[339053.609534] generic-usb 0003:046D:C01E.00B6: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[339053.690315] usb 2-4.2: new high speed USB device using ehci_hcd and address 45
[339053.803695] usb 2-4.2: configuration #1 chosen from 1 choice
[339053.804260] scsi55 : SCSI emulation for USB Mass Storage devices
[339053.804415] usb-storage: device found at 45
[339053.804417] usb-storage: waiting for device to settle before scanning
[339053.882808] usb 2-4.3: new high speed USB device using ehci_hcd and address 46
[339053.992823] usb 2-4.3: configuration #1 chosen from 1 choice
[339053.993193] scsi56 : SCSI emulation for USB Mass Storage devices
[339053.993351] usb-storage: device found at 46
[339053.993353] usb-storage: waiting for device to settle before scanning
[339054.072816] usb 2-4.4: new high speed USB device using ehci_hcd and address 47
[339058.704190] usb 2-4.4: configuration #1 chosen from 1 choice
[339058.704893] scsi57 : SCSI emulation for USB Mass Storage devices
[339058.705049] usb-storage: device found at 47
[339058.705051] usb-storage: waiting for device to settle before scanning
[339058.802761] usb-storage: device scan complete
[339058.803201] scsi 55:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[339058.803630] sd 55:0:0:0: Attached scsi generic sg5 type 0
[339058.807203] sd 55:0:0:0: [sdg] 15753215 512-byte logical blocks: (8.06 GB/7.51 GiB)
[339058.807675] sd 55:0:0:0: [sdg] Write Protect is off
[339058.807679] sd 55:0:0:0: [sdg] Mode Sense: 45 00 00 08
[339058.807681] sd 55:0:0:0: [sdg] Assuming drive cache: write through
[339058.810538] sd 55:0:0:0: [sdg] Assuming drive cache: write through
[339058.810544]  sdg: sdg1
[339058.813944] sd 55:0:0:0: [sdg] Assuming drive cache: write through
[339058.813949] sd 55:0:0:0: [sdg] Attached SCSI removable disk
[339058.990361] usb-storage: device scan complete
[339058.990960] scsi 56:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[339058.993202] sd 56:0:0:0: [sdj] 15769600 512-byte logical blocks: (8.07 GB/7.51 GiB)
[339058.994109] sd 56:0:0:0: [sdj] Write Protect is off
[339058.994112] sd 56:0:0:0: [sdj] Mode Sense: 23 00 00 00
[339058.994115] sd 56:0:0:0: [sdj] Assuming drive cache: write through
[339058.996926] sd 56:0:0:0: Attached scsi generic sg6 type 0
[339058.997940] sd 56:0:0:0: [sdj] Assuming drive cache: write through
[339058.997947]  sdj: sdj1
[339059.221411] sd 56:0:0:0: [sdj] Assuming drive cache: write through
[339059.221416] sd 56:0:0:0: [sdj] Attached SCSI removable disk
[339063.700475] usb-storage: device scan complete
[339063.701586] scsi 57:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[339063.703470] sd 57:0:0:0: Attached scsi generic sg7 type 0
[339063.705051] sd 57:0:0:0: [sdk] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[339063.707530] sd 57:0:0:0: [sdk] Write Protect is off
[339063.707534] sd 57:0:0:0: [sdk] Mode Sense: 43 00 00 00
[339063.707537] sd 57:0:0:0: [sdk] Assuming drive cache: write through
[339063.710572] sd 57:0:0:0: [sdk] Assuming drive cache: write through
[339063.710578]  sdk: sdk1
[339063.713573] sd 57:0:0:0: [sdk] Assuming drive cache: write through
[339063.713578] sd 57:0:0:0: [sdk] Attached SCSI removable disk
[339507.012637] npviewer.bin[12919]: segfault at 418 ip 00000000f6101a56 sp 00000000ffd2a4e8 error 6 in libflashplayer.so[f5eb3000+b04000]
[339580.039272] CE: hpet increasing min_delta_ns to 33750 nsec
[339819.829308] usb 2-2: USB disconnect, address 118
[339820.200630] usb 2-2: new high speed USB device using ehci_hcd and address 48
[339820.351662] usb 2-2: configuration #1 chosen from 1 choice
[339820.352213] scsi58 : SCSI emulation for USB Mass Storage devices
[339820.352364] usb-storage: device found at 48
[339820.352366] usb-storage: waiting for device to settle before scanning
[339821.238447] usb 2-2: USB disconnect, address 48
[339821.553754] usb 2-2: new high speed USB device using ehci_hcd and address 49
[339821.703144] usb 2-2: configuration #1 chosen from 1 choice
[339821.703729] scsi59 : SCSI emulation for USB Mass Storage devices
[339821.703904] usb-storage: device found at 49
[339821.703906] usb-storage: waiting for device to settle before scanning
[339826.703649] usb-storage: device scan complete
[339826.704174] scsi 59:0:0:0: Direct-Access     WD       2500BMV External 1.75 PQ: 0 ANSI: 4
[339826.704720] sd 59:0:0:0: Attached scsi generic sg3 type 0
[339826.707559] sd 59:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[339826.708807] sd 59:0:0:0: [sdc] Write Protect is off
[339826.708810] sd 59:0:0:0: [sdc] Mode Sense: 23 00 00 00
[339826.708813] sd 59:0:0:0: [sdc] Assuming drive cache: write through
[339826.710436] sd 59:0:0:0: [sdc] Assuming drive cache: write through
[339826.710442]  sdc:
[339826.812693] usb 2-2: USB disconnect, address 49
[339826.812839] sd 59:0:0:0: [sdc] Unhandled error code
[339826.812841] sd 59:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[339826.812845] sd 59:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[339826.812854] end_request: I/O error, dev sdc, sector 0
[339826.812859] Buffer I/O error on device sdc, logical block 0
[339826.814003] ldm_validate_partition_table(): Disk read failed.
[339826.814030] Dev sdc: unable to read RDB block 0
[339826.814074]  unable to read partition table
[339826.814246] sd 59:0:0:0: [sdc] READ CAPACITY failed
[339826.814248] sd 59:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[339826.814252] sd 59:0:0:0: [sdc] Sense not available.
[339826.814265] sd 59:0:0:0: [sdc] Assuming drive cache: write through
[339826.814268] sd 59:0:0:0: [sdc] Attached SCSI disk
[339833.540055] usb 2-2: new high speed USB device using ehci_hcd and address 50
[339833.691405] usb 2-2: configuration #1 chosen from 1 choice
[339833.691915] scsi60 : SCSI emulation for USB Mass Storage devices
[339833.692139] usb-storage: device found at 50
[339833.692141] usb-storage: waiting for device to settle before scanning
[339838.690254] usb-storage: device scan complete
[339838.690808] scsi 60:0:0:0: Direct-Access     WD       2500BMV External 1.75 PQ: 0 ANSI: 4
[339838.691269] sd 60:0:0:0: Attached scsi generic sg3 type 0
[339838.694136] sd 60:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[339838.696528] sd 60:0:0:0: [sdc] Write Protect is off
[339838.696532] sd 60:0:0:0: [sdc] Mode Sense: 23 00 00 00
[339838.696535] sd 60:0:0:0: [sdc] Assuming drive cache: write through
[339838.697938] sd 60:0:0:0: [sdc] Assuming drive cache: write through
[339838.697943]  sdc: sdc1
[339838.750039] sd 60:0:0:0: [sdc] Assuming drive cache: write through
[339838.750044] sd 60:0:0:0: [sdc] Attached SCSI disk
[339849.388820] usb 2-2: USB disconnect, address 50
[341324.094608] UDP: short packet: From 0.0.0.0:0 0/122 to 0.0.0.0:0
[341590.632629] npviewer.bin[16154]: segfault at 418 ip 00000000f602ba56 sp 00000000ff89a2a8 error 6 in libflashplayer.so[f5ddd000+b04000]
[341745.791900] npviewer.bin[19920]: segfault at f583404c ip 00000000f6193057 sp 00000000ff93dca0 error 4 in libflashplayer.so[f5df4000+b04000]
[342302.413840] npviewer.bin[22776]: segfault at 418 ip 00000000f60aba56 sp 00000000fff5d808 error 6 in libflashplayer.so[f5e5d000+b04000]
[343225.097395] npviewer.bin[32668]: segfault at 30 ip 00000000f5e5600d sp 00000000ffb03950 error 4 in libflashplayer.so[f5dfd000+b04000]
[343937.587729] npviewer.bin[17748]: segfault at 418 ip 00000000f604ca56 sp 00000000ff862a28 error 6 in libflashplayer.so[f5dfe000+b04000]
[346248.360347] npviewer.bin[12795]: segfault at 418 ip 00000000f60cba56 sp 00000000ff85bc28 error 6 in libflashplayer.so[f5e7d000+b04000]
[346450.342439] npviewer.bin[4476]: segfault at 87d8430 ip 00000000087d8430 sp 00000000ff9c11fc error 15
[346710.036211] UDP: short packet: From 0.0.0.0:29808 12147/151 to 0.0.0.0:14895
[346785.629586] UDP: short packet: From 0.0.0.0:1024 1024/151 to 0.0.0.0:0
[347271.079234] npviewer.bin[7906]: segfault at ed461054 ip 00000000f6235033 sp 00000000ffb15dd0 error 4 in libflashplayer.so[f5e96000+b04000]
[347600.971008] npviewer.bin[22350]: segfault at 418 ip 00000000f6107a56 sp 00000000fff09198 error 6 in libflashplayer.so[f5eb9000+b04000]
[349428.616525] UDP: short packet: From 0.0.0.0:39328 14480/151 to 0.0.0.0:2072
[355025.989916] UDP: short packet: From 0.0.0.0:0 0/151 to 0.0.0.0:0
[357703.530547] UDP: short packet: From 0.0.0.0:30018 10340/151 to 0.0.0.0:43361
[363073.703398] UDP: short packet: From 0.0.0.0:0 0/151 to 0.0.0.0:0
[368605.788585] UDP: short packet: From 0.0.0.0:1024 1024/122 to 0.0.0.0:0
[371228.239528] UDP: short packet: From 1.136.255.255:0 0/151 to 0.188.91.120:0
[371333.405503] UDP: short packet: From 0.0.0.0:0 0/151 to 0.0.0.0:0
[373710.545370] UDP: short packet: From 0.0.0.0:0 0/151 to 0.0.0.0:0
[373891.299459] UDP: short packet: From 0.0.0.0:0 0/151 to 0.0.0.0:0
[376464.599912] UDP: short packet: From 0.0.0.0:1024 1024/122 to 0.0.0.0:0
[378354.988570] npviewer.bin[2609]: segfault at ec16a054 ip 00000000f61e2033 sp 00000000ffd5c0a0 error 4 in libflashplayer.so[f5e43000+b04000]
[379110.293007] UDP: short packet: From 0.0.0.0:1024 1024/151 to 0.0.0.0:0
[379261.486289] UDP: short packet: From 0.0.0.0:0 0/122 to 0.0.0.0:0
mastershihochief@cortanamobile:~$ 
```

and as always the results for sudo make -f Makefile.standalone to build the kernel module


```
mastershihochief@cortanamobile:~$ cd '/home/mastershihochief/syntekdriver/tags/2.1.0/
> 
> ^C
mastershihochief@cortanamobile:~$ cd '/home/mastershihochief/syntekdriver/tags/2.1.0/'

mastershihochief@cortanamobile:~/syntekdriver/tags/2.1.0$ sudo make -f Makefile.standalone
[sudo] password for mastershihochief: 
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [driver] Error 2
mastershihochief@cortanamobile:~/syntekdriver/tags/2.1.0$ ^C
mastershihochief@cortanamobile:~/syntekdriver/tags/2.1.0$ 
```

---

### Post by okplayer02 on 2010-06-26
well i found instructions for your webcam and yes even though its an internal webcam on your laptop it still shows up in the lsusb

the website is from french users of ubuntu so you can translate or follow along even though i dont speak french i understand what they are doing. 

[http://doc.ubuntu-fr.org/syntek](http://doc.ubuntu-fr.org/syntek)

[http://trycatch.iblogger.org/software/syntek-webcam-driver-in-ubuntu](http://trycatch.iblogger.org/software/syntek-webcam-driver-in-ubuntu)

here is one in english

take a look there.

---

### Post by MasterShihoChief on 2010-06-27
It didnt work with what i did the first time for some reason:
```
mastershihochief@cortanamobile:~/Downloads/stk11xx-2.1.0$ make -f '/home/mastershihochief/Downloads/stk11xx-2.1.0/Makefile-syntekdriver' 
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/mastershihochief/Downloads/stk11xx-2.1.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-usb.o
  CC [M]  /home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.o
/home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.c:1737: error: unknown field &#8216;compat_ioctl&#8217; specified in initializer
/home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.c:1737: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
make[2]: *** [/home/mastershihochief/Downloads/stk11xx-2.1.0/stk11xx-v4l.o] Error 1
make[1]: *** [_module_/home/mastershihochief/Downloads/stk11xx-2.1.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2
mastershihochief@cortanamobile:~/Downloads/stk11xx-2.1.0$ 

```

But it did build it using the directions from the second link and starting over with svn instead of an archive.
```
mastershihochief@cortanamobile:~$ mkdir syntek </code> <code>cd syntek </code> <code>svn co https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driv
bash: syntax error near unexpected token `<'
mastershihochief@cortanamobile:~$ mkdir syntek
mastershihochief@cortanamobile:~$ cd syntek
mastershihochief@cortanamobile:~/syntek$ svn co https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/dri
^Csvn: PROPFIND of '/svnroot/syntekdriver/trunk/dri': SSL handshake failed: SSL error: Function was interrupted. (https://syntekdriver.svn.sourceforge.net)
mastershihochief@cortanamobile:~/syntek$ sudo svn co https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/dri
^Csvn: Caught signal
mastershihochief@cortanamobile:~/syntek$ sudo svn co https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver
A    driver/stk11xx-dev.c
A    driver/Kconfig
A    driver/stk11xx-dev-a311.c
A    driver/stk11xx-dev.h
A    driver/stk11xx-dev-6a31.c
A    driver/stk11xx-dev-a821.c
A    driver/stk11xx-dev-6a33.c
A    driver/stk11xx-dev-6a51.c
A    driver/stk11xx-usb.c
A    driver/README
A    driver/stk11xx-dev-6a54.c
A    driver/stk11xx-dev-6d51.c
A    driver/stk11xx.txt
A    driver/stk11xx-dev-0500.c
A    driver/Makefile.standalone
A    driver/stk11xx-bayer.c
A    driver/stk11xx-v4l.c
A    driver/stk11xx-dev-0408.c
A    driver/stk11xx-sysfs.c
A    driver/stk11xx.h
A    driver/Kbuild
A    driver/doxygen.cfg
A    driver/Makefile
A    driver/stk11xx-buf.c
Checked out revision 99.
mastershihochief@cortanamobile:~/syntek$ cd driver
mastershihochief@cortanamobile:~/syntek/driver$ wget http://bookeldor-net.info/merdier/Makefile-syntekdriver
--2010-06-28 02:28:31--  http://bookeldor-net.info/merdier/Makefile-syntekdriver
Resolving bookeldor-net.info... 213.186.33.48
Connecting to bookeldor-net.info|213.186.33.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 967 [text/plain]
Makefile-syntekdriver: Permission denied

Cannot write to `Makefile-syntekdriver' (Permission denied).
mastershihochief@cortanamobile:~/syntek/driver$ sudo wget http://bookeldor-net.info/merdier/Makefile-syntekdriver
--2010-06-28 02:28:40--  http://bookeldor-net.info/merdier/Makefile-syntekdriver
Resolving bookeldor-net.info... 213.186.33.48
Connecting to bookeldor-net.info|213.186.33.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 967 [text/plain]
Saving to: `Makefile-syntekdriver'

100%[======================================>] 967         --.-K/s   in 0s      

2010-06-28 02:28:41 (127 MB/s) - `Makefile-syntekdriver' saved [967/967]

mastershihochief@cortanamobile:~/syntek/driver$ make -f Makefile-syntekdriver
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/mastershihochief/syntek/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
mkdir: cannot create directory `/home/mastershihochief/syntek/driver/.tmp_versions': Permission denied
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-usb.o
Assembler messages:
Fatal error: can't create /home/mastershihochief/syntek/driver/.tmp_stk11xx-usb.o: Permission denied
make[2]: *** [/home/mastershihochief/syntek/driver/stk11xx-usb.o] Error 2
make[1]: *** [_module_/home/mastershihochief/syntek/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2
mastershihochief@cortanamobile:~/syntek/driver$ sudo make -f Makefile-syntekdriver
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/mastershihochief/syntek/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-usb.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-v4l.o
/home/mastershihochief/syntek/driver/stk11xx-v4l.c: In function &#8216;v4l_stk11xx_do_ioctl&#8217;:
/home/mastershihochief/syntek/driver/stk11xx-v4l.c:1241: warning: &#8216;pix_format.bytesperline&#8217; may be used uninitialized in this function
/home/mastershihochief/syntek/driver/stk11xx-v4l.c:1241: warning: &#8216;pix_format.sizeimage&#8217; may be used uninitialized in this function
/home/mastershihochief/syntek/driver/stk11xx-v4l.c:1241: warning: &#8216;pix_format.pixelformat&#8217; may be used uninitialized in this function
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-sysfs.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-buf.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-bayer.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-0408.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-0500.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-a311.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-a821.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-6a31.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-6a33.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-6a51.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-6a54.o
  CC [M]  /home/mastershihochief/syntek/driver/stk11xx-dev-6d51.o
  LD [M]  /home/mastershihochief/syntek/driver/stk11xx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mastershihochief/syntek/driver/stk11xx.mod.o
  LD [M]  /home/mastershihochief/syntek/driver/stk11xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
mastershihochief@cortanamobile:~/syntek/driver$ sudo make -f Makefile-syntekdriver install
mkdir -p /lib/modules/2.6.32-22-generic/kernel/drivers/usb/media
install -m 644 -o 0 -g 0 stk11xx.ko /lib/modules/2.6.32-22-generic/kernel/drivers/usb/media
depmod -a
mastershihochief@cortanamobile:~/syntek/driver$ sudo modprobe stk11xx
mastershihochief@cortanamobile:~/syntek/driver$ 

```

Only problem now is cheese still crashes and the system still cant use it or cant see it >_<
dmesg gives me this
```
[98594.068010] stk11xx: Syntek USB2.0 webcam driver startup
[98594.068012] stk11xx: Copyright(c) 2006-2009 Nicolas VIVIEN
[98594.068056] usbcore: registered new interface driver usb_stk11xx_driver
[98594.068465] stk11xx: v2.2.0 : Syntek USB Video Camera
[98611.140180] uvcvideo: Failed to query (130) UVC probe control : -110 (exp. 26).
[98611.141124] cheese[16313]: segfault at 0 ip (null) sp 00007fb159536ae8 error 14 in cheese[400000+28000]
[99069.320124] uvcvideo: Failed to query (130) UVC probe control : -110 (exp. 26).
[99070.520987] uvcvideo: Failed to query (129) UVC probe control : -110 (exp. 26).
[99071.662746] uvcvideo: Failed to set UVC commit control : -110 (exp. 26).
[99096.180746] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -110 (exp. 2).
[99096.480127] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -110 (exp. 2).
[99097.485589] cheese[24648]: segfault at 0 ip 00007f352ea1e052 sp 00007f3521888cb0 error 4 in libcheese-gtk.so.18.0.0[7f352ea0e000+17000]

```

---

### Post by okplayer02 on 2010-06-28
did you try this command with your webcam you go to the video tab and click on default input also under device to see if it recognizes it?

```
gstreamer-properties
```

---

### Post by MasterShihoChief on 2010-06-28
I get this and i tried all the plugins

```
mastershihochief@cortanamobile:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Custom': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src2:
system error: No such file or directory]

```

---

### Post by okplayer02 on 2010-06-29
run this command to see if the other module is still loaded

```
lsmod | grep stk-webcam
```

if it is then remove the module

```
rmmod stk-webcam
```

then confirm that the old module is not loaded

```
lsmod | grep stk-webcam
```

now load the module you built

```
sudo modprobe stk11xx
```

finally ```
dmesg |tail
```

now run
```
gstreamer-properties
```

when you click on the test button for the default input video device does the cam start up?

---

### Post by okplayer02 on 2010-06-29
suggestion i would also go to the upstream project where this syntek drivers are coming from and post in their mailing list also to see if your hardware is supported. just always good to not only ask here in ubuntu but in the upstream project.

---

### Post by MasterShihoChief on 2010-06-29
new errors lol

```
mastershihochief@cortanamobile:~$ lsmod | grep stk-webcam
mastershihochief@cortanamobile:~$ rmmod stk-webcam
ERROR: Module stk_webcam does not exist in /proc/modules
mastershihochief@cortanamobile:~$ sudo modprobe stk11xx
[sudo] password for mastershihochief: 
mastershihochief@cortanamobile:~$ dmesg |tail
[ 1171.008803] usb 2-4.1: USB disconnect, address 10
[ 1171.310430] usb 2-4.1: new low speed USB device using ehci_hcd and address 11
[ 1171.425539] usb 2-4.1: configuration #1 chosen from 1 choice
[ 1171.429620] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input13
[ 1171.429844] generic-usb 0003:046D:C01E.0005: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1/input0
[ 1234.294107] lo: Disabled Privacy Extensions
[ 1671.000844] stk11xx: Syntek USB2.0 webcam driver startup
[ 1671.000850] stk11xx: Copyright(c) 2006-2009 Nicolas VIVIEN
[ 1671.000951] usbcore: registered new interface driver usb_stk11xx_driver
[ 1671.000958] stk11xx: v2.2.0 : Syntek USB Video Camera
mastershihochief@cortanamobile:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]
libv4l2: error setting pixformat: Input/output error
Segmentation fault
mastershihochief@cortanamobile:~$ 

```

My webcam doesnt show up as a device in skype anymore as well. Before this it had showed up as the proper device as it does in windows but it was a black screen

dmesg shows this after trying to run cheese(note cheese did not instantly crash this time, it just has a black screen now):

```
[ 1671.000844] stk11xx: Syntek USB2.0 webcam driver startup
[ 1671.000850] stk11xx: Copyright(c) 2006-2009 Nicolas VIVIEN
[ 1671.000951] usbcore: registered new interface driver usb_stk11xx_driver
[ 1671.000958] stk11xx: v2.2.0 : Syntek USB Video Camera
[ 1715.950223] uvcvideo: Failed to query (130) UVC probe control : -110 (exp. 26).
[ 1715.951318] __ratelimit: 12 callbacks suppressed
[ 1715.951328] gstreamer-prope[4065]: segfault at 0 ip (null) sp 00007fb385d2bb28 error 14 in gstreamer-properties[400000+6000]
[ 2019.090134] uvcvideo: Failed to set UVC commit control : -110 (exp. 26).
[ 2027.943412] usb 1-1: USB disconnect, address 2
mastershihochief@cortanamobile:~$ 

```

---

### Post by okplayer02 on 2010-06-29
did you happen to look at the forums for this syntek webcam 


[http://sourceforge.net/projects/syntekdriver/forums/forum/616183](http://sourceforge.net/projects/syntekdriver/forums/forum/616183)

you should check here with the upstream project also. not to push you off to others but they would have more direct knowledge about your particular webcam.

---

### Post by okplayer02 on 2010-06-29
seems like you been at it for a while trying to get your cam to work when i searched here i seen you in another thread in regards to your webcam. thats ok i dont blame you :) but you really should work with the developers that are making this driver seems maybe or maybe not it supports your chipset so i suggest you contact them. 

[http://syntekdriver.sourceforge.net/index.php?mode=help_us](http://syntekdriver.sourceforge.net/index.php?mode=help_us)

that is the link.

---

