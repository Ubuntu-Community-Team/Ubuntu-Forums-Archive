---
title: "Serial Connections To Cisco Devices?"
date: 2010-04-22
forum: General Help
---

### Post by CarlosinFL on 2010-04-22
I would like to know what I can use on Ubuntu laptops and desktops to simply access all my Cisco network hardware via 'serial' comm ports? I use to open up a 'virtual' machine of Windows XP but that is getting too annoying at this point. Do you guys recommend an application that works on Ubuntu / Linux that allows me to access Cisco switches and routers?

---

### Post by Sef on 2010-04-22
Moved to General Help.

---

### Post by CarlosinFL on 2010-04-23
Anyone?

---

### Post by P4man on 2010-04-23
I have no idea.. does it require cisco software, or do you just need a serial terminal (something like gkterm) ?

---

### Post by Grenage on 2010-04-23
Doesn't it just use a basic terminal (like hyperterminal)?  Minicom is my app of choice, I use it on our switches here.

```
sudo apt-get install minicom
```

Edit: I believe Cutecom is an alternative option, it has a GUI; I've never tried it.

---

### Post by CarlosinFL on 2010-04-26
No I don't require a GUI so 'Minicom' sounds very nice. I will give it a try. I tried gtkterm before & hate the copy and paste method on that front end...

---

### Post by CarlosinFL on 2010-04-29
Thanks! Minicom worked great but I have a netbook which has no serial port. However I use my netbook to connect to Cisco network devices via serial to USB converter. I installed Minicom on my netbook and I don't know how I can tell Minicom to use my USB port rather than default to /dev/ttyS0.

Can anyone tell me how I can change or point Minicom to use my USB port so my serial to USB will work?

---

### Post by P4man on 2010-04-30
Is the usb serial port convertor working? If not, check this:

[http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

If its a matter of configuring minicom, then i cant help as I dont have it and cant install it atm.

---

### Post by Drenriza on 2010-04-30
use minicom to connect to cisco devices.
 
Works like a charm and has never had problems with it.

---

### Post by Grenage on 2010-04-30
> **CarlosinFL said:**
> Thanks! Minicom worked great but I have a netbook which has no serial port. However I use my netbook to connect to Cisco network devices via serial to USB converter. I installed Minicom on my netbook and I don't know how I can tell Minicom to use my USB port rather than default to /dev/ttyS0.

Can anyone tell me how I can change or point Minicom to use my USB port so my serial to USB will work?

Change your minicom config:

```
minicom -s
```

The port will likely be /dev/ttyUSB0 but it could be /dev/ttyUSB1 or above.

---

### Post by dpiddyTx on 2010-04-30
Just install putty and check the Serial checkbox, instead of telnet or ssh, and it should show up in your list of connections.  Otherwise, as Grenage already pointed out,  just check your /dev folder and you will see something similar to /dev/ttyS0 (serial) or /dev/ttyUSB0 etc ... once you launch putty just select "Serial" and then you can just copy/paste   "/dev/ttyS0" into the 'Serial line' textbox and hit connect.  If it's a Cisco box and your going for the console port, make sure your 'speed' in putty is set to 9600, which should be set by default in putty.

---

