---
title: "usb to serial adapter please help"
date: 2011-11-16
forum: General Help
---

### Post by wumethods8 on 2011-11-16
hi im trying to get my ysg to serial adapter working.I tied a couple things online with no luck.I have done the procedure to find out my vendor and prodct numbers.I do this command   sudo modprobe usbserial vendor=0x4348 product=0x5523  with my vendor and product number where it should be.and nothg happens.  This is what i get  

root@wayne-Inspiron-1520:/home/wayne# sudo modprobe usbserial vendor=0x4348 product=0x5523 
root@wayne-Inspiron-1520:/home/wayne# 
It just skips down to the starting line again.any thoughts or suggestions i would really appreciate it.thanks in advance.

---

### Post by wumethods8 on 2011-11-16
please help

---

### Post by Mark Phelps on 2011-11-16
Hey ... I can guess you're frustrated -- but quit bumping.  Doing that more than once in 24 hours is considered RUDE by community standards.  

This is a global forum, and the folks who could help you best just might be asleep right now.

So, have patience and give it some time.

---

### Post by efflandt on 2011-11-16
What does **lsusb** (like list usb) show for the device.  Maybe someone would recognize it from that and offer more help.

I have a USB to serial cable that Linux seemed to automatically recognize, but don't remember if I actually used it in Linux to access a 15+ year old Garmin GPS 45 because I don't think the Linux gps programs had a way to set that slow of a baud rate (9600 baud).  I did download its waypoints with the Windows Garmin Map program.

---

### Post by wumethods8 on 2011-11-17
here is what lsusb says when put it in.

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by njefsky on 2011-11-18
Hey,

Ubuntu 11.10?
I have isues there to 10.4 worked for me.
The driver loads.
You can check that to disconect the usb cabl, plug it back in and than type:
# dmesg
You see that the module is loaded.
/dev/ttyUSB0 is created.
But than you're stuck comunication is not working at all.

---

