---
title: "Cannot delete/modify printer URI"
date: 2010-07-01
forum: General Help
---

### Post by fopetesl on 2010-07-01
Breezy 5.10 (not upgradeable yet :( )
Am trying to delete one printer and install another.
With existing printer before deletion```
~# cat /etc/cups/printers.conf
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sun Feb 14 18:28:27 2010
<DefaultPrinter Photosmart>
Info 
Location 
DeviceURI beh:/1/0/30/usb:/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
```
...and...```
~# lpinfo -v
network socket
network beh
network bluetooth
network http
network ipp
network lpd
direct canon:/dev/lp0
direct epson:/dev/lp0
direct parallel:/dev/lp0
direct usb:/dev/usb/lp0
direct usb:/dev/usb/lp1
direct usb:/dev/usb/lp2
direct usb:/dev/usb/lp3
direct usb:/dev/usb/lp4
direct usb:/dev/usb/lp5
direct usb:/dev/usb/lp6
direct usb:/dev/usb/lp7
direct usb:/dev/usb/lp8
direct usb:/dev/usb/lp9
direct usb:/dev/usb/lp10
direct usb:/dev/usb/lp11
direct usb:/dev/usb/lp12
direct usb:/dev/usb/lp13
direct usb:/dev/usb/lp14
direct usb:/dev/usb/lp15
network smb
```[COLOR="Blue"]beh[/COLOR] is the backend error handler which keeps the printer 'live' if ever it's powered off when a print is requested :)
Now with the printer deleted using CUPS GUI (localhost:631) and the new one not installed the printer URIs get screwed up```
network socket
network beh
network bluetooth
direct hp:/no_device_found
network http
network ipp
network lpd
direct canon:/dev/lp0
direct epson:/dev/lp0
direct parallel:/dev/lp0
[COLOR="Red"]direct usb://CB770A?serial=CN9BACB10F05CT
direct usb://hp/deskjet%205550?serial=MY24T3M1YR2L
[/COLOR]direct usb:/dev/usb/lp2
direct usb:/dev/usb/lp3
direct usb:/dev/usb/lp4
direct usb:/dev/usb/lp5
direct usb:/dev/usb/lp6
direct usb:/dev/usb/lp7
direct usb:/dev/usb/lp8
direct usb:/dev/usb/lp9
direct usb:/dev/usb/lp10
direct usb:/dev/usb/lp11
direct usb:/dev/usb/lp12
direct usb:/dev/usb/lp13
direct usb:/dev/usb/lp14
direct usb:/dev/usb/lp15
network smb
```and whatever I try by installing another printer (HP Deskjet 5550) on what used to be direct usb:/dev/usb/lp0 it succeeds but will not print.
I guess because the printer URI doesn't match the serial number or usb://CB770A doesn't actually exist.

BTW I have _never_ used a printer type CB770A!
Installing the printer on other usb ports, lp1, lp2, etc., also fails to print.

Note that this Deskjet5550 works fine in Windoze and from Ubuntu 10.04 so it isn't a printer specific problem.

I have spent quite some time trying to find where the printer URIs are defined even using strace (which calls localhost so I lose trace) without success.

Anyone any suggestions as to how I can remove these ghost printer URIs?

---

