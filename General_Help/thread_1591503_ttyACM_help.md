---
title: "ttyACM help"
date: 2010-10-09
forum: General Help
---

### Post by RichardUK on 2010-10-09
I have a PLC that uses a USB -> serial converter for it's coms, this uses the ST Microelectronics chip st72f651

It comes up as /dev/ttyACM0 as well as /dev/serial/by-id/usb-STMicroelectronics_USB_to_Serial_bridge-if00


How can I use it as a com port? 

In windows XP it comes up as a com port, unfortunately for me the thing does not work in Vista 64bit or Win7 so I was really hoping Linux could save my bacon here. :)

Close but no cigar.

---

### Post by dcstar on 2010-10-09
> **RichardUK said:**
> I have a PLC that uses a USB -> serial converter for it's coms, this uses the ST Microelectronics chip st72f651

It comes up as /dev/ttyACM0 as well as /dev/serial/by-id/usb-STMicroelectronics_USB_to_Serial_bridge-if00


How can I use it as a com port? 

In windows XP it comes up as a com port, unfortunately for me the thing does not work in Vista 64bit or Win7 so I was really hoping Linux could save my bacon here. :)

Close but no cigar.

```
man getty
```

---

### Post by RichardUK on 2010-10-10
I need to open the port and write a raw set of characters to it, it is not a standard login type of connection. getty is of no use here.

---

### Post by dcstar on 2010-10-10
> **RichardUK said:**
> I need to open the port and write a raw set of characters to it, it is not a standard login type of connection. getty is of no use here.

A port is a port is a port. The getty system uses all ports the system makes available, it contains the interface for setting baud rate etc. which you need for any serial I/O.

This will give you some idea of what to do:

[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)
[http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

---

### Post by jwatte on 2012-05-25
> **dcstar said:**
> The getty system uses all ports the system makes available

I found this while looking for other information about ttyACM (for my Arduino,) and because I think it's wrong, and others may find it too (first page on Google,) I'll add my two cents:

The getty system uses nothing unless told to. Typically, getty is spawned by inittab. "grep getty /etc/inittab" on an old-school UNIX box, or "grep -r getty /etc/init" on a more modern Debian, will show how getty is spawned, and this almost never includes ttyACM. To talk to ttyACM, or any other serial port that's not already used by something else, you open it as a file descriptor (open() ...) and issue ioctl() on the file descriptor (man 4 tty_ioctl) or use tcgetattr/tcsetattr on the same.

If you want to set serial port attributes from the command line, "stty blah-blah < /dev/ttyACM0" can also do it.

---

### Post by ubudog on 2012-05-26
Back to sleep thread.

---

