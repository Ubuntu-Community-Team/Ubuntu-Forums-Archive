---
title: "USB to Serial Support Oneiric Ocelot"
date: 2012-02-11
forum: General Help
---

### Post by adpinto on 2012-02-11
Hi Ubuntu Team

Facing some issues with USB-Serial converter based on HL 340 - Ubuntu 11.10. Cannot communicate with Cisco 1751 router; PuTTy configured as serial, /dev/ttyUSB0, 9600, 8 bits, 1 stop-bit, none (parity), flow control XON/XOFf or None. I have tested router mgmt on WinXP but need this setup on Linux (GNS3).
I have found some threads such as [http://tiagovaz.wordpress.com/2008/0...-linux-kernel/](http://tiagovaz.wordpress.com/2008/0...-linux-kernel/) but they are from 2008; probably drivers are already supported on Oneiric, as seen below to facilitate investigation;  
Any support is welcomed !!! Many Thanks in advance.

Cheers,

adpinto

ls -l /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 0 2012-02-11 15:38 /dev/ttyUSB0

dmesg
[   10.712230] usbcore: registered new interface driver usbserial
[   10.712241] USB Serial support registered for generic
[   10.712292] usbcore: registered new interface driver usbserial_generic
[   10.712293] usbserial: USB Serial Driver core
[   10.721801] USB Serial support registered for ch341-uart
[   10.721821] ch341 3-1:1.0: ch341-uart converter detected
[   10.744207] usb 3-1: ch341-uart converter now attached to ttyUSB0
[   10.744225] usbcore: registered new interface driver ch341

lsusb
Bus 003 Device 002: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter
Bus 003 Device 003: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/m

sudo usb-devices
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1a86 ProdID=7523 Rev=02.52
S:  Product=USB2.0-Serial
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=96mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=02 Driver=ch341

lsmod |grep "usb"
usbhid                 47198  0 
hid                    95463  2 hid_sunplus,usbhid
usbserial              47107  1 ch341

---

### Post by pejcao on 2012-07-04
Same device, same issue. Any news?

---

### Post by wbosher on 2012-07-04
Have you tried the latest version of Ubuntu? Mine now works fine after upgrading to 12 from 11.
 
Still doesn't work in Putty, but Minicom is great.  :)

---

### Post by pejcao on 2012-07-06
It used to work on 11.04, now on l2.04 (3.2.0-26-generic-pae) It doesn't (nor screen or minicom or putty)
BTW, this is my devive:

Bus 004 Device 003: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter

---

### Post by Cheesehead on 2012-07-06
1) Make sure you're not running getty and terminal program on the same machine and port. One machine must run getty (only), the other must run terminal (only).

2) Getty does not autoconfigure speeds, so make sure both getty and terminal are configured for similar speed and settings.

3) Make sure you're not using a really cheap serial-to-USB adaptor. Some that claim to be pl2303's are counterfeit, not fully compatible, and make life much harder than they need to be.

Obvious, but it's amazing how often the problem is something simple...

---

### Post by wbosher on 2012-07-08
It is a cheap and crappy device, but it is exactly the same as what I'm using **(ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter)** and mine works fine in Minicom.
 
I'm also connecting to Cisco routers/switches. 
 
What do you mean by "can't communicate"? Strange symbols, or nothing at all?

---

