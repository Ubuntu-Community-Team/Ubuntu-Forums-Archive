---
title: "Garmin EtrexH Having conection problems"
date: 2011-07-06
forum: General Help
---

### Post by Johnread on 2011-07-06
Hi 

I have a Garmin EtrexH,  with a Garmin PC Interface cable with a 9 pin serial female "D" type on the end. 
Plugged into a logilink serial to USB converter Part Number AU0002B

lsusb shows 

```


xxx@Packard-Bell-EasyNote:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 005: ID 03ee:6901 Mitsumi SmartDisk FDD
Bus 001 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xxx@Packard-Bell-EasyNote:~$ 


```When I try to connect, I get the following error

```


xxx@Packard-Bell-EasyNote:~$ gpsbabel -i garmin -f usb
[ERROR] XSERIAL: Cannot open serial port 'usb': No such file or directory
[ERROR] Cannot open serial port 'usb'
GARMIN:Can't init usb

xxx@Packard-Bell-EasyNote:~$ sudo gpsbabel -i garmin -f usb
[sudo] password for xxx: 
[ERROR] XSERIAL: Cannot open serial port 'usb': No such file or directory
[ERROR] Cannot open serial port 'usb'
GARMIN:Can't init usb
xxx@Packard-Bell-EasyNote:~$ 


```Thanks for any help  you can provide.

---

