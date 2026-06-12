---
title: "Installing Nokia Phone As Modem"
date: 2010-11-15
forum: General Help
---

### Post by ndeoligence on 2010-11-15
Hi guys,
 
I recently installed Linux UBUNTU Version 10.04 into my laptop (HP Pavilion dv7-4065, which came with Windows 7 Home Premium pre-installed).
I am still new to Ubuntu, and I don't have any programming knowledge.
mistakenly, I messed up my Win7 while installing Linux and I can't get it to boot anymore.
But anyways, that's not what I would like help with - Just trying to prove my programming incompetence
and also to reveal that I don't have anywhere else to boot.
So my problem is that I need internet connection with my Laptop through my cellphone.
I have a Nokia X6 phone, service provider=MTN SouthAfrica.
I managed to find a post that helped significantly with the problem (from: [http://symbianism.blogspot.com/2008/10/linux-and-symbian-pc-suite-alternatives.html](http://symbianism.blogspot.com/2008/10/linux-and-symbian-pc-suite-alternatives.html)), but then I got stuck at the command:
 
sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)
 
because Linux tells me that it couldn't find [some file] (i'm not sure what the filename is, but it's a Ubuntu modem manager).
 
So... could anyone please tell me where and/or how i can get it and how to install it.
Otherwise, could one tell me of a different way of making my Ubuntu recognize my phone as a modem.
Also, How is it done through Bluetooth - because that was through the USB cable?
I apreciate any input, in advance...

---

### Post by TNT1 on 2010-11-15
I have two nokia's, one mtn, one vodacom, both are pretty much plugnplay for me.

---

### Post by Hippytaff on 2010-11-15
With the phone plugged in via usb, what is the output of
```

lsusb

```
this will tell you what ubuntu thinks the usb device is. A good starting point :-)

---

### Post by virgo977virgo on 2010-11-16
See if my reply to the thread *[Using Nokia N8 for mobile internet on 10.10]("http://ubuntuforums.org/showpost.php?p=10059602&postcount=3")* to use the Nokia N8 as a USB modem can help you.


Bye

---

