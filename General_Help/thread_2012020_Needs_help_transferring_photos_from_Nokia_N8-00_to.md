---
title: "Needs help transferring photos from Nokia N8-00 to Ubuntu 12.04 via USB"
date: 2012-06-28
forum: General Help
---

### Post by boxcorner on 2012-06-28
I have a Lenovo Z570 laptop running Ubuntu 12.04 plus Nokia N8-00 phone.

I want to transfer photo files from my phone to my laptop.  Nokia's software doesn't support Linux so I must dual boot into Windows 7 just to transfer photos.

With Ubuntu, I can transfer photos from the phone to my laptop wirelessly via Bluetooth but it is painfully slow.

With Ubuntu, whenever I connect the phone to my laptop using a Nokia CA-179 USB cable apparently it is not recognised as a device or drive.

I have installed Wammu via the Software Centre but it appears to hang whenever I try to use it, consequently I have needed to use System Monitor to kill the process.

How can I get Ubuntu to recognise the phone so I can transfer files via USB?

---

### Post by boxcorner on 2012-06-29
I have found a way to access the phone's file system:

Ubuntu Software Centre > gMobileMedia (Mobile Media Browser) > Preferences > Connection Port: /dev/ttyUSB0 > Connection type: at115200 > Phone model: autodetect > OK

then on the phone, select: Settings > Connnectivity > USB Mass storage mode > Use phone as modem: Active > Mass Storage: active

from gMobileMedia > Connect

result: 
a USB icon, called 15 GB File system, appears on the desktop 
then Shotwell starts automatically
in the left-hand column of Shotwell: Cameras > Mass Storage Camera
you should see some of your photos displayed here.

next, close Shotwell, then on the phone, select: Settings > Connectivity > USB Mass storage mode > Media transfer: Active

result:
two phone icons appear on the desktop, both called N8-00
then two pop-up windows are displayed, both containing text saying:
"You have just inserted a digital audio player. Choose what application to launch."
Ignore/close one of them, then in the drop-down menu of the other, select: Open Folder, and click on OK.
This will cause Nautilus to be launched.
In the left-hand column of Nautilus, select the uppermost (ie first) N8-00 icon, then expand the folder called 'Images'. 

This appears to allow access to all photos on the phone, not just the ones taken using Nolkia's camera application, but also ones stored by 3rd party photo applications (for example: PhotoFusion, PhotoTwister, ShutterPro, etc).

Hopefully this info will be of interest to someone ...

---

