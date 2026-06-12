---
title: "Vodafone k3565"
date: 2011-01-09
forum: General Help
---

### Post by npsilva on 2011-01-09
Hi,

I have installed Ubuntu 10.10 in my laptop. However, I have troubles with the Vodafone Huawei K3565. 

Anyone knows why I can only connect that 3g internet if I connect the pen to the laptop before turn on the computer... If I connect the 3g pen driver after the login in the Ubuntu that connection does not appear in the network  manager... 

best regards

Nuno

---

### Post by alexfish on 2011-01-09
HI

Re: Known Maverick Meerkat issues/bugs with workarounds
**3g broadband dongles**:


some of these devices are been reported : "[COLOR=Blue]not recognized on the system[/COLOR]" or "[COLOR=Blue]will not configure[/COLOR]"

this is due to the option driver module not loading

as a workaround the option driver can be loaded from the terminal


[**How to check for the option drive****r and modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

**Update :** Mon Oct 25 : 2010

**ZTE** devices not switching : above link updated with fix

these problem usually disappears by keep the system updated

**Update:** Sat Oct 23 : 2010

There  have been reports of devices Freezing ( under use ) hence can no longer  connect : the above link has been updated (Don,t moan it is NOT A FIX )  as each device is different
However I have tested one such device  and have used Sakis3g to reconfigure a ZTE 626 {successful} : may also  help with preparing Some CDMA devices


**FROM**:

**[B]Sticky:**[/B] [Known Maverick Meerkat issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1588889")

alexfish

---

### Post by npsilva on 2011-01-10
Hi,

thank you for the reply to my previous message. 

My problem remains... and seems that is a permission problem!!! because if I connect the device after the login into the ubuntu that device does not appear on the network manager. However if I put the device before turn on the computer everything works fine....

best regards

npsilva

> **alexfish said:**
> HI

Re: Known Maverick Meerkat issues/bugs with workarounds
**3g broadband dongles**:


some of these devices are been reported : "[COLOR=Blue]not recognized on the system[/COLOR]" or "[COLOR=Blue]will not configure[/COLOR]"

this is due to the option driver module not loading

as a workaround the option driver can be loaded from the terminal


[**How to check for the option drive****r and modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

**Update :** Mon Oct 25 : 2010

**ZTE** devices not switching : above link updated with fix

these problem usually disappears by keep the system updated

**Update:** Sat Oct 23 : 2010

There  have been reports of devices Freezing ( under use ) hence can no longer  connect : the above link has been updated (Don,t moan it is NOT A FIX )  as each device is different
However I have tested one such device  and have used Sakis3g to reconfigure a ZTE 626 {successful} : may also  help with preparing Some CDMA devices


**FROM**:

**[B]Sticky:**[/B] [Known Maverick Meerkat issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1588889")

alexfish

---

### Post by pjalegria on 2011-01-10
Install the package usb-modeswtich and usb-modeswtich-data

---

### Post by npsilva on 2011-01-11
> **pjalegria said:**
> Install the package usb-modeswtich and usb-modeswtich-data


I already have that packages installed.

---

### Post by alexfish on 2011-01-12
> **npsilva said:**
> Hi,

thank you for the reply to my previous message. 

My problem remains... and seems that is a permission problem!!! because if I connect the device after the login into the ubuntu that device does not appear on the network manager. However if I put the device before turn on the computer everything works fine....

best regards

npsilva

Hi

this device (k3565) is Notorious for ( as they say misbehaving )
and will as behave in different manor depending which kernel is been used,
if you look up the how to in my previous post, it mentions the different behavior (attitude)
mainly due to the possible firmware of the device
Check in a windows machine for updates

in the "how to" there is a post on setting the behavior of the cd masstorage (can  disable),this can help with some of the stability issues it has with the kernel, as it has a habit of presenting multiples,of it self
on the system.

at one stage "As a final resort" in ubuntu 9.10 , I thought bugger it, and reset the device to factory defaults
Although this is not recommended , " putting back into a windows comp reloaded the firmware".

you mention K3565 , there may be two varieties (ZTE and Huawie).
which one is it

alexfish

---

### Post by npsilva on 2011-01-13
Hi, 

my device is from Huawei.



> **alexfish said:**
> Hi

this device (k3565) is Notorious for ( as they say misbehaving )
and will as behave in different manor depending which kernel is been used,
if you look up the how to in my previous post, it mentions the different behavior (attitude)
mainly due to the possible firmware of the device
Check in a windows machine for updates

in the "how to" there is a post on setting the behavior of the cd masstorage (can  disable),this can help with some of the stability issues it has with the kernel, as it has a habit of presenting multiples,of it self
on the system.

at one stage "As a final resort" in ubuntu 9.10 , I thought bugger it, and reset the device to factory defaults
Although this is not recommended , " putting back into a windows comp reloaded the firmware".

you mention K3565 , there may be two varieties (ZTE and Huawie).
which one is it

alexfish

---

### Post by alexfish on 2011-01-14
can post details of this command from the terminal

Code:
[COLOR=Blue]
usb-devices[/COLOR]

locate the lines which indicate the device and post only those lines

---

### Post by npsilva on 2011-01-14
usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1003 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0458 ProdID=0036 Rev=01.10
S:  Manufacturer=Genius
S:  Product=NetScroll + Mini Traveler
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub



> **alexfish said:**
> can post details of this command from the terminal

Code:
[COLOR=Blue]
usb-devices[/COLOR]

locate the lines which indicate the device and post only those lines

---

### Post by alexfish on 2011-01-16
hi

from part of the list 

T: Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=1003 Rev=00.00
S: Manufacturer=HUAWEI Technology
S: Product=HUAWEI Mobile
C: #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

when in this state will it connect
if connecting 
can post detail of same usb-devices command , when it does not work

---

### Post by npsilva on 2011-01-17
Sorry for this delay.


usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1003 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0458 ProdID=0036 Rev=01.10
S:  Manufacturer=Genius
S:  Product=NetScroll + Mini Traveler
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub





> **alexfish said:**
> hi

from part of the list 

T: Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=1003 Rev=00.00
S: Manufacturer=HUAWEI Technology
S: Product=HUAWEI Mobile
C: #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

when in this state will it connect
if connecting 
can post detail of same usb-devices command , when it does not work

---

### Post by alexfish on 2011-01-17
hi

can check this out

[**How to check for the option drive****r and modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

alexfish

---

### Post by npsilva on 2011-01-19
> **alexfish said:**
> hi

can check this out

[**How to check for the option drive****r and modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

alexfish


I'm a beginner in Linux / Ubuntu user. So I didn't find the solution of my problem in the link that alexfis post in the previous answer... Can anyone tell me explicit how to solve my problem?


best regards

npsilva

---

### Post by npsilva on 2011-01-19
> **alexfish said:**
> hi

can check this out

[**How to check for the option drive****r and modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

alexfish


I'm a beginner in Linux / Ubuntu user. So I didn't find the solution of my problem in the link that alexfis post in the previous answer... Can anyone tell me explicit how to solve my problem?


best regards

npsilva

---

### Post by alexfish on 2011-01-23
> **npsilva said:**
> I'm a beginner in Linux / Ubuntu user. So I didn't find the solution of my problem in the link that alexfis post in the previous answer... Can anyone tell me explicit how to solve my problem?


best regards

npsilva

have you tried


from your info

this idicates the option module has loaded

> I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


this indicates the option module  fail to load

> I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

when in this state open up the terminal and enter the following code

```
sudo modprobe option
```

can also try this
```

sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```

look for 

> # Huawei E220, E230, E270, E870
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="usb_modeswitch '%b/%k'"

and insert line so the bits look like

> # Huawei E220, E230, E270, E870
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="usb_modeswitch '%b/%k'"
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="/sbin/modprobe option"

save and exit

what happens

check the results with the

```
usb-devices
```

---

### Post by npsilva on 2011-01-23
> **alexfish said:**
> have you tried


from your info

this idicates the option module has loaded



this indicates the option module  fail to load


when in this state open up the terminal and enter the following code

```
sudo modprobe option
```can also try this
```

sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```look for 


and insert line so the bits look like



save and exit

what happens

check the results with the

```
usb-devices
```

Hi,

my problem is now solved. Thank you very much for our help.

thanks

Npsilva

---

