---
title: "Weather Station - Which port is this ?"
date: 2010-03-20
forum: General Help
---

### Post by Kevbert on 2010-03-20
I want to try to use a La Crosse weather station with Ubuntu and am having a few basic problems. The weather station is connected to the PC via a serial to USB adapter. If I connect it I get the following in terminal:
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**[COLOR="Red"]Bus 002 Device 010: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port[/COLOR]**
Bus 002 Device 009: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 002 Device 007: ID 0001:0000 Fry's Electronics 
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
Which port is the one highlighted ? (in the form /dev/ttyUSB0)
How can I determine that the Weather Station is sending info to my PC ?

---

### Post by nunojpg on 2010-03-20
How many /dev/ttyUSBx do you have?

If you only have one(probably, if you only have that USB devices plugged), it's that. Not sure if this is a answer for your question.

You can start opening the serial port with "cu" or "minicom"

For cu:

sudo apt-get install cu
cu -l /dev/ttyUSB0 -s 9600(if that is the speed)

Then you should start seeing data if it streams by default. Otherwise you may need to query it with some command. Check the manual.

(quick tip: to exit cu enter "~.")

Regards

---

### Post by Kevbert on 2010-03-20
Thanks for the reply. Unfortunately cu just comes up with
```
$ cu -l /dev/ttyUSB0 -s 9600
Connected.
```
and nothing else. Other ports up to ttyUSB6 display that the 'line is in use'.
I've found that this is set up and shown in /var/log/messages.
It looks as if I'm not getting any data through.

---

### Post by nunojpg on 2010-03-20
What is the output of "ls /dev/ttyUSB*" when you have the station plugged and unplugged?

Have you read the manual? The last station I used(vaisala), I needed to configure several things.

---

### Post by Kevbert on 2010-03-20
The output when plugged in
```
$ ls /dev/ttyUSB0
/dev/ttyUSB0
```

When unplugged
```
$ ls /dev/ttyUSB0
ls: cannot access /dev/ttyUSB0: No such file or directory
```

This relates to the USB to serial interface and not to connecting or disconnecting the weather station itself (as that has no effect). I know the interface works fine in Windows XP.
The output from /var/log/messages
```
Mar 20 14:30:14 kevin-dt1b kernel: [16912.829020] usb 2-6: new full speed USB device using ohci_hcd and address 11
Mar 20 14:30:14 kevin-dt1b kernel: [16913.042867] usb 2-6: configuration #1 chosen from 1 choice
Mar 20 14:30:14 kevin-dt1b kernel: [16913.044147] pl2303 2-6:1.0: pl2303 converter detected
Mar 20 14:30:15 kevin-dt1b kernel: [16913.077189] usb 2-6: pl2303 converter now attached to ttyUSB0
Mar 20 14:30:53 kevin-dt1b kernel: [16951.272274] usb 2-6: USB disconnect, address 11
Mar 20 14:30:53 kevin-dt1b kernel: [16951.274614] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
Mar 20 14:30:53 kevin-dt1b kernel: [16951.274631] pl2303 2-6:1.0: device disconnected
```
The weather station is a La Crosse WS2350. The manual doesn't have details on how to install software in Linux, only Windows, but I know that running the WS2350 is possible with Ubuntu.

---

### Post by nunojpg on 2010-03-20
I wrote "ls /dev/ttyUSB*" not "ls /dev/ttyUSB0".

I wonder where all that serial ports(ttyUSB1-6) come from...

Anyway, what software do you want to install? You can look for some compatible software, or start checking the serial port interface commands? The manual should explain all that.
Then try to enter that commands with cu.

---

### Post by Kevbert on 2010-03-20
```
$ ls /dev/ttyUSB*
/dev/ttyUSB0
```
So just one ttyUSB...
Which manual ? The manual that came with the WS is pretty basic and specifically for WinXP/Win2000.
Can you recommend any software for Ubuntu that you've had success with ?

---

### Post by nunojpg on 2010-03-20
I went to check and in fact it doesn't explain anything about PC connection.
I used a weather station but only with a script to save data...I can't help on finding software.


I see you have 3 options:
Ask the manufacturer about the spec and develop your own software for whatever you need.
Spy the communication in a windows PC and learn the protocol.
Google "La crosse linux".

Regards

---

### Post by Kevbert on 2010-03-20
Thanks for the help. I'll have to persist in trying to get either Open2300 or wview working.

---

