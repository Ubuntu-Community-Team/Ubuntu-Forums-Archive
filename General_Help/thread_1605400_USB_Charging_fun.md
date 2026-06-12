---
title: "USB Charging fun"
date: 2010-10-25
forum: General Help
---

### Post by cannywizard on 2010-10-25
I have a wireless headset that I'm trying to charge through USB. When I connect it, it just doesn't charge. I've found losts of similar posts here, but they're not much help.

Looking at dmesg, the device isn't recognised, which is not surprising, since I think the USB port is only for charging, and it won't communicate over USB.
lsusb also tells me that (apart from other things that are connected to the USB bus, that all of the 'MaxPower' variables are set to 0mA.

So what I think is happening is I connect the headset ubuntu queries it, receives no reply, and so doesn't let the port draw any current. As far as I'm aware, there usually is some kind of OS handshaking like this, but it may vary from model of computer to model, so there's no point in saying "my <INSERT USB DEVICE HERE> charges"
I am able to charge my MP3 player from the same port (because it's recognised), and I can charge the headset if I use a dumb mains->USB/5V transformer, but it should also work with my laptop.

What I think I need is some way of manually setting the 'MaxPower' on the USB ports.
Anyone know of a way to do this?

---

### Post by sanderd17 on 2010-10-25
Does this thread helps?
[http://ubuntuforums.org/showthread.php?t=853179]("http://ubuntuforums.org/showthread.php?t=853179")

What you need to do is:

```

gksudo nautilus

```

go to /sys/bus/usb/devices/, open one of your USB divices (you can adjust the power of one if you always put your charger in the same port, just do trial and error to find the port), open the direcotry "power" with in it 3 files, open the file "level" with a text editor and change the contents to "on" (without quotes).

---

### Post by cannywizard on 2010-10-26
I had not found that page before, thanks.

But....

The power directory only has one file in it 'wakeup'

Trying to do 
```
sudo echo on > level
```gets me
```
bash: level: No such file or directory
``````
sudo touch level
```is the same.

And editing 'wakeup' doesn't work.

Incidentally, this is the output from dmesg after I connect the device. I'm wondering if the missing files is due to the lack of enumeration
```
[23027.096020] usb 6-1: new full speed USB device using uhci_hcd and address 2
[23027.217285] usb 6-1: device descriptor read/64, error -71
[23027.440170] usb 6-1: device descriptor read/64, error -71
[23027.657253] usb 6-1: new full speed USB device using uhci_hcd and address 3
[23027.780162] usb 6-1: device descriptor read/64, error -71
[23028.008131] usb 6-1: device descriptor read/64, error -71
[23028.224165] usb 6-1: new full speed USB device using uhci_hcd and address 4
[23028.636158] usb 6-1: device not accepting address 4, error -71
[23028.804172] usb 6-1: new full speed USB device using uhci_hcd and address 5
[23029.216036] usb 6-1: device not accepting address 5, error -71
[23029.216148] hub 6-0:1.0: unable to enumerate USB device on port 1
```

---

### Post by sanderd17 on 2010-10-26
Sorry, I can't be of further use, from here on I'll have to ask google for help. And since you seem to be not a Linux noob, I think you can do this yourself.

---

### Post by cannywizard on 2010-10-27
Cool, cheers anyway.

---

