---
title: "Wireless Modem Configuration for UTL in Ubuntu"
date: 2009-09-19
forum: General Help
---

### Post by captainpirate on 2009-09-19
I am using wireless internet services in Nepal provided by UTL.
It uses a CDMA modem which has its own driver also which mainly supports windows platform.
My problem is that how can i configure it in ultimate ubuntu 2.0.
Please provide me solution in details.

---

### Post by sudeepkc on 2009-10-05
I also have same problem and i found this in mazzako forum...i hope it works

Good news to CDMA users with chinese USB device.
A friend of mine pointed that linux does support chinese USB cdma device, its just that wvdial doesn't get them in first go. From his advice I have succesfully connected to cdma from ubuntu. Here is what you do

First check that your device is supported in Ubuntu. That is once you've inserted the USB device, you should get a 
/dev/ttyUSB0 device

$ ls /dev/ttyUSB* 
If the result is
/dev/ttyUSB0 , then ur lucky mate.

Now you have to modify the /etc/wvdial.conf file. In terminal do
$ gksudo gedit /etc/wvdial.conf

here is how my file looks like (for UTL CDMA)
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 230400
Init1 = ATE0
#Init2 = AT$PBTYPE=1 RPTCON=1 MTRPTTYPE=3 SMSRUIM=0 SMSTYPE=1
Init3 = AT+CTA=0
Init4 = ATEOV1
Init5 = AT
Init6 = ATS0=0
ISDN = 0
Modem Type = Analog Modem
Phone = #777
Username = [EMAIL="myphonenumber@utlnepal.com"]myphonenumber@utlnepal.com[/EMAIL]
Password = myphonenumber
Stupid Mode = 1
New PPPD = yes

Save it and then dial
$ sudo wvdial

after about 15-20 seconds it should give you the ip address, enjoy mate.

Cheers

---

