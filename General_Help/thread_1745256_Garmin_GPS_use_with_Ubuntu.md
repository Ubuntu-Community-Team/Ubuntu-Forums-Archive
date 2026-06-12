---
title: "Garmin GPS use with Ubuntu"
date: 2011-04-30
forum: General Help
---

### Post by Bellomo on 2011-04-30
Hi guys

Ive been trying to get ubuntu to recognise my garmin gps 60 device. Ive managed to set permissions for it (i think..) as well as it shows up on dmesg as 

[14563.410020] USB Serial support registered for Garmin GPS usb/tty
[14563.410343] garmin_gps 5-1:1.0: Garmin GPS usb/tty converter detected
[14563.411636] usb 5-1: Garmin GPS usb/tty converter now attached to ttyUSB0
[14563.411666] usbcore: registered new interface driver garmin_gps
[14563.411669] garmin_gps: v0.33:garmin gps driver
[14957.048106] usb 5-1: USB disconnect, address 3
[14957.048374] garmin_gps ttyUSB0: Garmin GPS usb/tty converter now disconnected from ttyUSB0
[14957.048396] garmin_gps 5-1:1.0: device disconnected
[14970.964054] usb 5-1: new full speed USB device using uhci_hcd and address 4
[14971.116207] usb 5-1: configuration #1 chosen from 1 choice
[14971.119612] garmin_gps 5-1:1.0: Garmin GPS usb/tty converter detected
[14971.119713] usb 5-1: Garmin GPS usb/tty converter now attached to ttyUSB0

so I can only assume, that its being recognized. however when I start either tangogps or gpsdrive they both say 'no gps'. 
I did have this working perfectly the other day, which baffles me as to why it would simply stop working 0.o

if it helps at all heres the output of me querying the permissions: 


root@michael-laptop:~# ls -l /dev/bus/usb/005/004
crw-rw----+ 1 root plugdev 189, 515 2011-05-01 13:05 /dev/bus/usb/005/004


tango gps seems to connect to gpsd just fine, its just getting the gps recognised. 

.. any ideas?

---

