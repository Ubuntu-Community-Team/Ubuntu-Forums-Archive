---
title: "need help with connecting to a serial port"
date: 2012-05-10
forum: General Help
---

### Post by wallybsams on 2012-05-10
I have been using a program to control my home lights and appliances for years,  had hardware trouble and now have a new computer, new CM11 interface  A new install of Ubuntu 12.4 32 bit os

I moved my application to the new machine ad tried to connect to the serial port
Error  "  serial port /dev/ttyS0 does not exist "

in a terminal I ran:

```
wally@wally:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.646129] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.069314] 00:03: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```checking for user, group and permissions:

```
wally@wally:~$ ls -l /dev/ttyS0
crw-rw-r-x 1 root dialout 4, 64 May 10 17:26 /dev/ttyS0
```I checked to make sure that the user wally is in the group dialout

this is the strange part:

I tried to open the port from terminal

```
wally@wally:~$ open /dev/ttyS0
openvt: Unable to open /dev/tty8: Permission denied
```I dont understand why the report says that tty8  was denied when I tried to open ttyS0

When I am in my control software and try to connect to /dev/ttyS0  it says  port does not exist

I will appreciate any suggestions

thank you
wsams  :confused:

---

