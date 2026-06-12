---
title: "Usbserial not installed in Ubuntu 10.10?"
date: 2010-10-19
forum: General Help
---

### Post by MemorX on 2010-10-19
Hi,

I am a fairly new user to Linux, and have a question about the following command:

cat /proc/tty/driver/usbserial

This has shown me a list of usb-serial devices and their respective ttyUSBx numbers, however it seems that this doesn't work in 10.10 (32-bit Desktop version).

I have tried using the lsusb command, but I cant get it to show the information I need.

How would one go about installing the program nessecary to run the command?

Thank you :)

---

### Post by alexfish on 2010-10-19
hi

Can you try

Code:

[COLOR=Blue]usb-devices[/COLOR]

and

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]

which type of device are you trying to identify

alexfish

---

### Post by MemorX on 2010-10-19
Hi,

And thanks for your answer.
I couldn't find the information I was looking for...
BTW, the devices I am looking for are USB to Serial Converters.

This one I got no response from:
> root@ask3:/# ls -al /dev/serial/by-id/usb*
ls: cannot access /dev/serial/by-id/usb*: No such file or directory

Here is an example (from an older Debian server):

> ask2:~# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0403:6001 Future Technology Devices International, Ltd 8-bit FIFO
Bus 001 Device 002: ID 0403:6001 Future Technology Devices International, Ltd 8-bit FIFO
Bus 001 Device 001: ID 0000:0000  

ask2:~# cat /proc/tty/driver/usbserial
usbserinfo:1.0 driver:2.0
0: module:ftdi_sio name:"FTDI USB Serial Device" vendor:0403 product:6001 num_ports:1 port:1 path:usb-0000:00:04.2-1
1: module:ftdi_sio name:"FTDI USB Serial Device" vendor:0403 product:6001 num_ports:1 port:1 path:usb-0000:00:04.2-2
ask2:~# 

How does one know what ttyUSBx the devices are using without usbserial, I have found no way to corrolate the information of the two commands?

---

### Post by alexfish on 2010-10-19
have you connected the device you are trying to identify

added

also try a file search on file system

ftdi , see if any  ftdi * .ko show up

---

### Post by MemorX on 2010-10-19
> **alexfish said:**
> have you connected the device you are trying to identify

added

also try a file search on file system

ftdi , see if any  ftdi * .ko show up

Ops,

Thanks, It was connected to the older server, I was under the impression that it would just print a blank table when nothing usb-serial like was connected. 
In stead it acted like it never existed.

---

### Post by alexfish on 2010-10-19
> **MemorX said:**
> Ops,

Thanks, It was connected to the older server, I was under the impression that it would just print a blank table when nothing usb-serial like was connected. 
In stead it acted like it never existed.

OOPs:guitar:

---

