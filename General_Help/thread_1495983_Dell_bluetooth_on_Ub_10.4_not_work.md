---
title: "Dell bluetooth on Ub 10.4 not work"
date: 2010-05-28
forum: General Help
---

### Post by dada_dmcmd on 2010-05-28
[SIZE="2"]hi community
[/SIZE]
[SIZE="2"]I have a problem on my dell latitude laptop
the bluetooth device was work good on ubuntu 9.10
I have ubuntu 10.4 now and bluetooth device work once by chance on it now when i open the blueman it gives me this massage:
[/SIZE]
**[SIZE="3"][CENTER]Bluez daemon is not running, blue man-manager cannot continue[/CENTER][/SIZE]**
[SIZE="2"]
I searched here and there and I tried many solutions and it still not work
:confused:
can any one help me........[/SIZE]

---

### Post by vandorjw on 2010-05-28
try this

> 
sudo apt-get install bluez bluez-utils 


---

### Post by matty_muso on 2010-07-15
Hi there,

Having the same problem on my Dell Latitude D810. Bluetooth worked fine in 9.04 but isn't working with 10.4. I get the error message:

Connection to Bluez Failed
Bluez daemon is not running, blueman-manager cannot continue.
This probably means that there were no Bluetooth adapters detected or Bluetooth daemon was not started.

When I type in terminal sudo blueman-applet it gets stuck on the following:

UpdatePowerState (/usr/lib/python2.6/dist-packages/blueman/plugins/applet/PowerManager.py:176)
off False 
foff False 
on True 
current state True 
new state True

If I start blueman-applet via a custom launcher, it shows that it is sleeping in system monitor-processes, but won't display.

Please help!

---

