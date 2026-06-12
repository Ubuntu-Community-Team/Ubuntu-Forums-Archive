---
title: "USB Serial  troubleshooting FTDI eee PC"
date: 2010-04-16
forum: General Help
---

### Post by markbann on 2010-04-16
Trying to find some basic help here.  Using an eee pc Asus 900A working with a usb to serial adapter (ftdi chip).  
lsusb and dmesg report the device is installed but how can I corroborate that?
The software I am using (easydnc) doesn't see the port and I am trying to determine if it is the software or the port.
Shouldn't I see something in the dev directory?
How can I tell what the port is called, /dev/ttyUSB0 or what?

---

### Post by akakingess on 2010-04-16
I'm just shooting into the dark here, but wouldn't you have to actually have something hooked up to that port in order for easydnc to see it. Sorry if I misunderstood, but that was just the first thought that came to mind.

---

### Post by markbann on 2010-04-16
Don't know.  I did have the it connected to the CNC machine though at one time and it still didn't see it.

---

### Post by markbann on 2010-04-16
when I do a ls -l  *USB*
I see the USB0 in the tts folder
But the software says dev/tts/USB0 is missing.  I did notice that the group for USB0 is "root", not "tty" like the other ports.

---

### Post by markbann on 2010-04-16
I plugged in an old serial modem.  cat /dev/tts/USB0 and cat /dev/ttyUSB0 both turn lights on on the modem, so I assume that means it is sending something out to through it.....

---

### Post by markbann on 2010-04-16
Is it perhaps that I don't have the correct driver installed?  This is from the driver readme but I thought it meant I didn't have to install a driver with a  newer kernel:
[COLOR="DarkOrange"]Instructions to install new driver

You may require the sources matching the current kernel to be installed on your system (and built). 
There are many helpfull websites that can assist you with this step and it isnt as daunting as you first think!
Try [http://www.osnews.com/story.php?news_id=2949&page=2](http://www.osnews.com/story.php?news_id=2949&page=2) as a first step if the link is still available.


To install the ftdi_sio driver use the following steps:

1. Create a temporary folder in your linux machine.
2. Extract the files from ftdi_sio.tar.gz file to your temporary folder
	"gunzip ftdi_sio.tar.gz"
	"tar -xvf ftdi_sio.tar"
3. Build the driver
	"make"
4. Plug in your ftdi device
5. Check to see if default driver was loaded
	"lsmod" - you will see ftdi_sio if a driver is loaded
6. Remove the default installed driver
	"rmmod ftdi_sio"
7. Install the newly built driver
	"insmod ftdi_sio.o"


NOTES: 
	1.This driver was adapted from the 2.4.32 kernel to support both the 2232C and 232R chip
	2.There is no need to follow this procedure if you want 232R chip supprt. The 232BM driver will 
	be sufficient.Changes made to the driver for the 232R chip are purly cosmetic (plug/unplug will appear as a 232R chip in 
	the kernel log).[/COLOR]

---

