---
title: "Automatic kernel module loading"
date: 2011-07-14
forum: General Help
---

### Post by jslabl on 2011-07-14
I have a pc running ubuntu 10.04 2.6.32-31-generic kernel and my problem is that whenever I plug in any usb device while the pc is running, it's kernel module is not loaded automatically though I can still load it manually using modprobe.

Here's an example using a 4GB USB drive:[INDENT]> 
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=03 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0930 ProdID=6545 Rev=01.00
S:  Manufacturer=Kingston
S:  Product=DataTraveler G3
S:  SerialNumber=00142238268CEB21451D0039
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
[/INDENT]When I plug it in before booting, the module is loaded normally and I am able to use the device. 

I have another identical pc that was configured a few months before with kernel 2.6.32-26-generic, and on this one, the LKMs are loaded automatically when a device is plugged in. 

I have downloaded kernel sources and used menuconfig to see configuration but I couldn't find the automatic kernel module loading option. 

I would greatly appreciate it if someone would help enlighten me as to what may cause my problem.

JS

I think I posted this in the wrong forum, could a mod move this thread to the newbie forum please ?

---

