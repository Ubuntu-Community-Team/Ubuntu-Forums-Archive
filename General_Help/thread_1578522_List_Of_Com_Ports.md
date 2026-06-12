---
title: "List Of Com Ports"
date: 2010-09-20
forum: General Help
---

### Post by PressureWave on 2010-09-20
Hello,

Ive searched Google for this (what i thought was a) simple answer, but there's nothing out there that i could find.

All i need is to see a list, window or anything that shows all of the serial (rs232) com ports that are on my Ubuntu 10.04 machine and what their associated port numbers are.

I have one com port that is on the motherboard (so obviously its com 1) and it works fine.

but i also have a usb to serial (FTDI) com port that i cant figure out what the port number is...

any help would be great

---

### Post by afrowildo on 2010-09-20
Your USB-to-Serial adapter probably won't be recognised as serial, rather it will be picked up as a USB device.

---

### Post by Bachstelze on 2010-09-20
Normally, serial ports are /dev/tty<something>. "Real" serial ports should  be /dev/ttyS<somenumber>. Your USB-to-serial might be something else, like /dev/ttyUSB0.

---

### Post by PressureWave on 2010-09-20
ok i went to /dev/ and i see ttys0 - ttys3 and ttyUSB0

now im wondering if i have 4 "real" com ports and one usb com port?????

if com's 0 - 3 are already in use then does that make ttyUSB0 the fourth com port (or com 5)???

[EDIT]

im trying to write a little script in Python, i configured it to open the fourth port (aka com 5), when i execute the script it generates an error stating that there is no such file as ttys4... How would i direct it to open ttyUSB0?? if that is the right file

---

### Post by Bachstelze on 2010-09-20
That means you have four software serial ports. Not all of them are necessarily "wired" to a hardware serial port.

The COMn notation is only for Windows. In Linux, serial ports are /dev/tty*, not COMn.

---

