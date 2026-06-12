---
title: "USB Device Permissions"
date: 2009-12-01
forum: General Help
---

### Post by lazerradial2003 on 2009-12-01
I'm writing a python app using pyusb which needs access to a USB device (it's a data logger with no linux driver). The python script works but have to run it as root to give it access to the USB Device. 

Does anyone know how to change the permissions to allow my user full access to the device (and ideally but less importantly allow the virtualbox user full access).

---

### Post by lazerradial2003 on 2009-12-03
Anyone?

---

### Post by kostaben on 2009-12-03
Don´t know if i get right your question but what if you do chmod 775 (read execute) or chmod 777 (read write execute)and then the path to the usb?

---

### Post by kostaben on 2009-12-03
As for the numbers after the chmod command look here:
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by lazerradial2003 on 2009-12-03
Thanks for the reply, do you know how I find the path to the relevant USB device?

---

### Post by kostaben on 2009-12-03
if you right click on the usb and choose properties, you can find it in there. Should be in /media but i am not sure and i dont have a linux machine here.

---

### Post by lazerradial2003 on 2009-12-03
Thanks, think is it's not a mass storage device or similar. It's a data logger (made by Lascar) and there aren't any linux drivers for it. I used SnoopyPro in windows to see which commands are sent to it when various operations are performed on it and then pyusb in Python to simulate these commands under linux. The script works great but can only access the USB device if run using sudo. Because the script is going to be built into a much larger project it isn't feasable to just run the whole thing as root so I need to allow the logged in user access to the device if that makes any sense!

---

### Post by stefangr1 on 2009-12-03
> **lazerradial2003 said:**
> I'm writing a python app using pyusb which needs access to a USB device (it's a data logger with no linux driver). The python script works but have to run it as root to give it access to the USB Device. 

Does anyone know how to change the permissions to allow my user full access to the device (and ideally but less importantly allow the virtualbox user full access).


In Ubuntu, the usb permissions are arranged in:

/etc/udev/rules.d

You can't just chown the usb device directly.


First you run:

lsusb

This gives you the device id. Example:
Bus 001 Device 005: ID 03f0:3404 Hewlett-Packard DeskJet 6122

You need the vendor id, in this example: 03f0
and the device id, in this example: 3404

Now add a textfile called 50-datalogger.rules to the folder /etc/udev/rules.d  containing:
(change yourusername to your username)

cut---------------------------------------------------------------


SUBSYSTEM !="usb_device", ACTION !="add", GOTO="datalogger_rules_end"

SYSFS{idVendor} =="03f0", SYSFS{idProduct} =="3404", SYMLINK+="datalogger"

MODE="0666", OWNER="yourusername", GROUP="root"

LABEL="datalogger_rules_end"


cut----------------------------------------------------------------


and execute:
chmod 4755 /path/yourapplication
chown yourusername /path/yourapplication

No 100% guarantee, but I think this is how it works...

---

### Post by hopews on 2010-06-29
Some lascar usb data loggers seem to be very similar (I assume same manafacturer, though I can't tell who is the original) to ones by measurement computing (mccdaq.com) and they list this site as having linux drivers for them:  [ftp://lx10.tx.ncsu.edu/pub/Linux/drivers/](ftp://lx10.tx.ncsu.edu/pub/Linux/drivers/)

Hopefully that helps.

---

### Post by captomner on 2011-01-05
I tried doing this with a Velleman K8055 kit, and I was unable to get the permissions set correctly. Since it's a different topic, I started a new thread, and if anyone is able to help, I'd really appreciate it.

[http://ubuntuforums.org/showthread.php?t=1660136]("http://ubuntuforums.org/showthread.php?t=1660136")

---

### Post by wilderbeest on 2011-09-30
Hi there,

I've got a Lascar EL-USB-5 and I would love to run this thing on Ubuntu - at the moment, I have a Windows VM just to use it.

Could you please send me or post the python code? It would be much appreciated.

Best regards,

Christian

---

### Post by tormod on 2011-10-21
There is no point in setting mode 0666 (write access for anybody) and at the same time assign the device to a specific user.

I would recommend giving permission to the "plugdev" group which covers all desktop users and is used for typical pluggable devices. Also nowadays you should match on ATTRS and not SYSFS. So all you need is:

```
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="3404", MODE="660", GROUP="plugdev"
```

BTW the chmod 4755/chown stuff in an earlier post is wrong and useless. Just make sure your application/script is executable with "chmod +x".

---

