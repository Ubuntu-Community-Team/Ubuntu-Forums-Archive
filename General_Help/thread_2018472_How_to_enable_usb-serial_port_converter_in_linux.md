---
title: "How to enable usb-serial port converter in linux"
date: 2012-07-06
forum: General Help
---

### Post by The Realist on 2012-07-06
Hello,  

I'm trying to use cutecom to read data from my serial port device - a fishfinder. I don't have a 9-pin port on my computer, so I am using a usb-serial port adapter. For windows, all I had to do was run a driver that came with the adapter  (which doesn't work with Linux). I can successfully output data to  Hyperterminal in Windows.

I found an article titled "How to enable USB-serial port adapter (RS-232) in Ubuntu linux." 

[http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

I followed its instructions exactly - I found the vendor and product id for the adapter and mapped it to /dev/tty/USB0.  Unfortunately, cutecom still will not communicate with the serial port device.

Does anybody know what the problem could be, or what I should do? Could it be a hardware compatibility issue?

I can give some more information if you need it. Thanks.

---

### Post by Cheesehead on 2012-07-06
Usually it's [FONT="Courier New"]/dev/ttyUSB0[/FONT], not [FONT="Courier New"]/dev/tty/USB0[/FONT] (note the extra slash in the second).

1) When you connect your Serial-to-USB adapter, try the command [FONT="Courier New"]dmesg | tail -n10[/FONT], which will give you the last 10 kernel messages. Look to see that the adapter has been recognized.

For example, here's what happens when I plug in my adapter:
```
$ dmesg | tail -n12
[COLOR="DimGray"][769979.109535] usb 2-1: USB disconnect, device number 2
[769979.109547] usb 2-1.1: USB disconnect, device number 3[/COLOR]
[777259.136075] usb 2-1: new full speed USB device number 4 using ohci_hcd
[777259.760230] usbcore: registered new interface driver usbserial
[777259.760314] USB Serial support registered for generic
[777259.765684] usbcore: registered new interface driver usbserial_generic
[777259.765701] usbserial: USB Serial Driver core
[777259.798969] USB Serial support registered for pl2303
[777259.801819] pl2303 2-1:1.0: pl2303 converter detected
[777259.825210] usb 2-1: pl2303 converter now attached to ttyUSB0
[777259.827598] usbcore: registered new interface driver pl2303
[777259.827612] pl2303: Prolific PL2303 USB to serial adaptor driver

```
The first two lines (in [COLOR="DimGray"]gray[/COLOR]), have an older timestamp - they are older, unrelated messages. You can see the process: First a USB device is detected, then the usbcore driver recognizes it, then the usbserial driver recognizes it, and finally the pl2303 driver recognizes it and attaches it to (/dev/)ttyUSB0

If yours is still not recognized, please post the result from [FONT="Courier New"]dmesg[/FONT] here.

---

