---
title: "usb cdma broadband"
date: 2010-01-15
forum: General Help
---

### Post by dodo_dodder on 2010-01-15
i have satanic ubuntu 8. i was trying to connect to my reliance netconnect broadband+ via the following method. the process failed. its a usb broadband dongle thing.

```
theunknowndoor@theunknowndoor:~$ SU
bash: SU: command not found
theunknowndoor@theunknowndoor:~$ su
Password: 
su: Authentication failure
theunknowndoor@theunknowndoor:~$ sudi -i
bash: sudi: command not found
theunknowndoor@theunknowndoor:~$ sudo -i
root@theunknowndoor:~# lsusb
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 064e:a129 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 19d2:fff5  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@theunknowndoor:~# modprobe usbserial vendor=0x19d2 product=0xfff5
root@theunknowndoor:~# gedit /etc/wvdial.conf
```
wvdial.conf after editing with username and password :

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB0
Username = 09326605205
Password = 09326605205
CBaud = 460800

in a seperate terminal attempt to connect :

```
theunknowndoor@theunknowndoor:~$ sudo wvdial
[sudo] password for theunknowndoor: 
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Is a directory
--> Cannot open /dev/ttyUSB0: Is a directory
--> Cannot open /dev/ttyUSB0: Is a directory
theunknowndoor@theunknowndoor:~$ 
```
---------------------------
this is because i tried to mkdir /dev/ttyUSB0

before that I made the directory an attempt to wvdial said cant find file . HELP!

---

### Post by GeorgeVita on 2010-01-20
Hi **dodo_dodder**,
at first boot without the modem and remove that directory: **sudo rmdir /dev/ttyUSB0**

As your modem is listed as 'Bus 002 Device 002: ID **19d2:fff5**' use it as a search string to find more help. A similar thread I found >>> [that]("http://ubuntuforums.org/showthread.php?t=1320700&highlight=19d2%3Afff5") <<< but for Ubuntu 9.04

Do the following test to determine system activity:
- Boot without modem, **wait** for the system to load
- open a terminal window (Applications>Accessories>Terminal) and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- attach modem, **wait** 30 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**
- copy all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and lsusb, post it here.

Check last dmesg output for: [ ...] sr 5:0:0:0: **Attached scsi CD-ROM sr0 **
and use: **sudo eject sr0** (replace sr0 with any sr**X** found)
Try again **lsusb** looking for changed productID 19d2:xxxx

Regards,
George

---

