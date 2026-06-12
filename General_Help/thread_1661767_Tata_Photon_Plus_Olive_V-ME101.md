---
title: "Tata Photon Plus Olive V-ME101"
date: 2011-01-07
forum: General Help
---

### Post by avanga on 2011-01-07
Hello,
I've resently switched to Tata Photon Plus(olive V-ME101). It works fine in windows.
But Since past one week I'm unable to install it in my ubuntu 10.10. The customer service fellows of tata also doesn't know how to do it. I've done installing through wvdial but of no use. My device isn't getting detected as usb modem. It is detecting as generice multi card when i plug in the device and start my lappy. Can any 1 pleaase help me out in this. I'm very much attracted to ubuntu 10.10 and I can't do anything if my usb doesn't works in it.
[COLOR=Red]**PLEASE HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**[/COLOR]

---

### Post by Vtechie on 2011-01-13
Try the following

**sudo apt-get update**
after updating the repositary list
enter
**sudo apt-get install usbmount**
this will enable u to automatically mount usb drive.
plug in ur tata photon+.Wait for few secnds and u will be able to see it has been mounted as thumb drive. If u open the drive u will be able to find the manual file Olive_VME101_User Manual.doc
or else do the following
**sudo apt-get install wvdial**
Now plug in your modem in USB port. On inserting you will notice icon of VME101 on your desktop screen, right click on it and eject it. 
1.In terminal write the following command:
$sudo lsusb
Sometimes it need to input the password for sudo, such as 
[sudo] password for ***: 
Please input it, then it should has similar information as follows:
Bus 002 Device 002: ID 201e:2009
Here the 201e:2009 is very important; it corresponds to the VID&PID of the data card.
1.Now it should load the proper module to let the kernel know the device. Please do as follows:
**$sudo modprobe usbserial vendor=0x201e product=0x2009** 
After that, using the command “dmesg” to check again, it will see the following information:
[COLOR="Cyan"]usbcore: registered new interface driver usbserial
drivers/usb/serial/isb-serial.c: USB Serial support registered for generic
usbserial_generic 2-2:1.0 generic converter detected
usb 2-2: generic converter now attached to ttyUSB0
usbserial_generic 2-2:1.1 generic converter detected
usb 2-2: generic converter now attached to ttyUSB1
usbserial_generic 2-2:1.2 generic converter detected
usb 2-2: generic converter now attached to ttyUSB2
usbcore: registered new interface driver usbserial_generic
drivers/usb/serial/usb-serial: USB Serial Driver core
[/COLOR]
1.Edit the wvdial configure file by typing the following command:
**[COLOR="Black"]$sudo gedit  /etc/wvdial.conf[/COLOR]**
On entering the above line a new window will pop up. Fill in the details as given below and click save and close that window.
Edit the wvdial.conf file as follows:
[Dialer Defaults]
Init = ATZ
Init = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 115200
Modem = /dev/ttyUSB0
Phone = #777
Username = internet
Password = internet
Stupid Mode = 1

save and exit
Do the wvdial to connect data service:
**$sudo wvdial**
This command will initialize the modem and connect you to internet.
hit ctrl+c to disconnect.
Now
1.Plug in your device and you will notice the dialer on desktop , right click on the dialer and eject it.     (Ejecting is compulsory )
2.On task Manger right click on the icon highlighted and select the option “**Edit Connections** “.
New window “**Network Connections**” will open > select **Mobile Broadband** option as displayed, then click on “**Add**” option
2.Select Forward without changing anything from drop down box:
Select Forward again without changing anything from drop down box:
Select **TATA Indicom (Photon+)** option & click on Forward:
Select “**Apply**”
After clicking “**Apply**” new window will pop up as displayed in picture below:
Fill the following details:-
Username –internet (small letters)
Password- internet (small letters)
Check the option “Connect automatically” & “Available to all users”, then click “Apply”.

Now u will be able to connect using gui.
Note that each time u cnnct it u would have to eject the drive and connect it.

Enjoy

---

### Post by avanga on 2011-01-13
Errors were encountered while processing:
 firmware-b43-installer
 crossplatformui
localepurge: Disk space freed in /usr/share/locale: 368 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 368 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
------------------------------------------------------------------------

the above error occured while installing usbmount. After i plug in the usb nothing happens.

---

### Post by Vtechie on 2011-01-13
just directly go to second step of installing **[COLOR=Black]wvdial[/COLOR]** .
Note that u need to have a working internet connection to install the apps.

---

### Post by saurabhkamshetty on 2011-08-26
its a very simple method guys ..
Install WINE software 1.3 version..
Not only photon it supports all d windows applications...
just install it, plug in and start surfing ...:p:p...

---

