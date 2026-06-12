---
title: "My 3G mobile internet pen stopped working on my PC with Ubuntu 10.10"
date: 2010-12-11
forum: General Help
---

### Post by Tina_E on 2010-12-11
Hi!

From one day to the other it crashed... So, I've deleted the link and when I try to install it again the PC failed to detect the device... But it works on windows...  Even when I try to put my card on a device of the same operator, it works in a Toshiba with Ubuntu 10.10 but not on mine PC... :confused: I've an ASUS F3Sseries and all of the updates installed.

I hope you can help me...


Thanks,
Tina

---

### Post by alexfish on 2010-12-11
hi

lets see if the device can be detected and rule out a faulty , usb interface

from the Menus top left , select Applications / Accesories / Terminal

Copy or enter these codes then press enter

Code:

[COLOR=Blue]lsusb [/COLOR]

post the results

then

[COLOR=Blue]usb-devices[/COLOR]

look for for lines which may indicate the device and post only those lines

post the results

if nothing showing in the above can try

code:

[COLOR=Blue]grep usbcore /var/log/dmesg

[COLOR=Black]**and or**[/COLOR]

ls -al /sys/kernel/debug/usb/usbmon
[/COLOR]
post the results

Can you confirm if any other usb devices are recognized IE: usb memory stick etc .
also have you tried other usb ports.

alexfish

---

### Post by Tina_E on 2010-12-13
Hi! Thanks for your reply,

The device is recognized:
(lsusb) 
Bus 005 Device 007: ID 0af0:6971 Option Globetrotter HSDPA Modem

(usb-devices)
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0af0 ProdID=6971 Rev=00.00
S:  Manufacturer=Option N.V.
S:  Product=Globetrotter HSDPA Modem  
S:  SerialNumber=Serial Number
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso

All other usb devices are recognized and I tried all usb ports.

But not always the device is on the list when I try to create a new mobile connection. When it appears and I can create the connection, I can't link... The icon lights moving, trying to connect, but it stops and doesn't connect to the Internet.

---

### Post by alexfish on 2010-12-13
Hi

You say . have Ubuntu 10.10 on laptop , Which version is on PC

you also mention "link" can you explain ,

is it just the connection in Network Manager or some other software that creates the link
before using Network manager

also mention " it crashed " are you saying the device was connecting and now does not connect

if it was working ; did the device fail to connect after updating the system

can also check which version of network manager on each system "right click the appelet About"

Can also post details of this command from the terminal before the connection is attempted

Code:
[COLOR=Blue]grep modem-manager /var/syslog [/COLOR]

then try this code:to monitor the connection

Code:
[COLOR=Blue]tail -f /var/log/syslog[/COLOR]

now try the connection

Check both systems see if can spot something different

but post only the results of the system where the device will not connect


alexfish

---

### Post by Tina_E on 2010-12-13
Hi, sorry for may bad explanation... I'll try to be more explicit:

"You say . have Ubuntu 10.10 on laptop , Which version is on PC"
When a said 'PC' I should said laptop...
 
 "you also mention "link" can you explain"
I mean that I can not establish connection to the Internet through the device.
 
 "is it just the connection in Network Manager or some other software that creates the link 
  before using Network manager"
It's just the Network Manager that creates the link

 "also mention " it crashed " are you saying the device was connecting and now does not connect"
Yes, the device was connecting and suddenly is not connecting anymore... (But it still works on windows!)
 
 "if it was working ; did the device fail to connect after updating the system"
I can't remember...

I have the Network Manager version 0.8.1 on my Asus laltop and on Toshiba laptop the 0.8 version

I try to do [COLOR=Blue]grep modem-manager /var/syslog [/COLOR]and the file or directory doesn't exist... (I have [COLOR=Blue]grep[/COLOR] installed)

[COLOR=Blue]tail -f /var/log/syslog[/COLOR]
Dec 13 18:36:14 Tina-PC modem-manager: supports_port: assertion `task == NULL' failed
Dec 13 18:36:14 Tina-PC modem-manager: (tty/ttyHS2): ignoring port unsupported by physical modem's plugin
Dec 13 18:36:14 Tina-PC modem-manager: Exported modem  /sys/devices/pci0000:00/0000:00:1d.1/usb6/6-2 as  /org/freedesktop/ModemManager/Modems/3
Dec 13 18:36:14 Tina-PC modem-manager: (/org/freedesktop/ModemManager/Modems/3): data port is hso0
Dec 13 18:36:14 Tina-PC NetworkManager[968]: <info> (hso0): new GSM device (driver: 'hso' ifindex: 39)
Dec 13 18:36:14 Tina-PC NetworkManager[968]: <info> (hso0): exported as /org/freedesktop/NetworkManager/Devices/9
Dec 13 18:36:14 Tina-PC NetworkManager[968]: <info> (hso0): now managed
Dec 13 18:36:14 Tina-PC NetworkManager[968]: <info> (hso0): device state change: 1 -> 2 (reason 2)
Dec 13 18:36:14 Tina-PC NetworkManager[968]: <info> (hso0): deactivating device (reason: 2).
Dec 13 18:36:14 Tina-PC NetworkManager[968]: <info> (hso0): device state change: 2 -> 3 (reason 0)

Thanks, Tina_E

---

### Post by langesmalle on 2010-12-17
@Tina_E:

Did you have any luck to get it working?
What did you do?

@others:

My Globetrotter  HSPDA USB modem is well recognized by Kubuntu 10.10

:~$ lsusb
Bus 005 Device 013: ID 0af0:6971 Option Globetrotter HSDPA Modem

:~$ usb-devices
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 13 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0af0 ProdID=6971 Rev=00.00
S:  Manufacturer=Option N.V.
S:  Product=Globetrotter HSDPA Modem  
S:  SerialNumber=Serial Number
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=hso

When I plug in the device I get following in /var/log/syslog:

Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS1) opening serial device...
Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS1): probe requested by plugin 'Option High-Speed'
Dec 17 15:12:45 Dell-D830 modem-manager: supports_port: assertion `task == NULL' failed
Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS2) opening serial device...
Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS2): probe requested by plugin 'Generic'
Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS0) opening serial device...
Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS0): probe requested by plugin 'Option High-Speed'
Dec 17 15:12:45 Dell-D830 modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1 claimed port hso0
Dec 17 15:12:45 Dell-D830 modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1
Dec 17 15:12:45 Dell-D830 modem-manager: (tty/ttyHS2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1
Dec 17 15:12:45 Dell-D830 modem-manager: (tty/ttyHS2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1
Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS3) opening serial device...
Dec 17 15:12:45 Dell-D830 modem-manager: (ttyHS3): probe requested by plugin 'Option High-Speed'
Dec 17 15:12:48 Dell-D830 modem-manager: (ttyHS1) closing serial device...
Dec 17 15:12:48 Dell-D830 modem-manager: (ttyHS0) closing serial device...
Dec 17 15:12:48 Dell-D830 modem-manager: (ttyHS3) closing serial device...
Dec 17 15:12:48 Dell-D830 modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1 claimed port ttyHS1
Dec 17 15:12:48 Dell-D830 modem-manager: (tty/ttyHS2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1
Dec 17 15:12:48 Dell-D830 modem-manager: (ttyHS0) opening serial device...
Dec 17 15:12:48 Dell-D830 modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1 claimed port ttyHS0
Dec 17 15:12:48 Dell-D830 modem-manager: (tty/ttyHS2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1
Dec 17 15:12:48 Dell-D830 modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1 claimed port ttyHS3
Dec 17 15:12:48 Dell-D830 modem-manager: (tty/ttyHS2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1
Dec 17 15:12:48 Dell-D830 modem-manager: (tty/ttyHS2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1
Dec 17 15:12:48 Dell-D830 modem-manager: (ttyHS0) closing serial device...
Dec 17 15:12:57 Dell-D830 modem-manager: (ttyHS2) closing serial device...
Dec 17 15:12:58 Dell-D830 modem-manager: (ttyHS2) opening serial device...
Dec 17 15:13:01 Dell-D830 modem-manager: (ttyHS2) closing serial device...
Dec 17 15:13:01 Dell-D830 modem-manager: supports_port: assertion `task == NULL' failed
Dec 17 15:13:01 Dell-D830 modem-manager: (tty/ttyHS2): ignoring port unsupported by physical modem's plugin
Dec 17 15:13:01 Dell-D830 modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1 as /org/freedesktop/ModemManager/Modems/6
Dec 17 15:13:01 Dell-D830 modem-manager: (/org/freedesktop/ModemManager/Modems/6): data port is hso0

But Networkmanager seems not to recognize the modem.
I need to add manually the settings and I&#7743; unable to make a connection with the device.

Anyone who can help me out of here.

Thnx in advance.

---

### Post by Tina_E on 2010-12-30
@langesmalle

I didn't have any luck, it still not working. I suppose that we have the same problem or a similar problem, but unfortunately I don't know yet how to solve it...

And I don't know how but my laptop usually causes damage on hard disk and it did it again... Not even my laptop works now...

Tina_E

---

