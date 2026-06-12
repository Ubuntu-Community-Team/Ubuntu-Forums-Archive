---
title: "Connect Phone to Laptop"
date: 2011-11-29
forum: General Help
---

### Post by techbrainless on 2011-11-29
Hi All,
How to connect the mobile phone to laptop (by the way i want to use this phone as gsm modem to configure it with kannel) 

I am using
1. Ubuntu 10.10
2. Sony erricson xperia mini 10
3. USB cable to connect from phone to laptop
when I execute lsusb command , I found that the usb is detected each time I plug it to laptop

---

### Post by techbrainless on 2011-11-29
Hi All,
Any reply

---

### Post by VeeDubb on 2011-11-29
I think there's no responses because you haven't asked a question yet.

---

### Post by techbrainless on 2011-11-29
Thanks VeeDubb for your reply,

While trying to connect sony ericsson xperia x10 mini (usb cable) to ubuntu 10.10  the SD card inside the phone appears but I can't get something like /dev/ttyACM to communicate with the phone.


My question is : How to get something like get something like /dev/ttyACM to communicate with the phone ?

---

### Post by VeeDubb on 2011-11-30
If you really mean using it as a dial-up modem, I can't be much help.  If you mean using it for internet using the phones's internet connection, you need to enable tethering on your phone, which may involve installing 3rd party software, and may also involve either rooting your phone or paying an additional subscription fee to your cell provider.

Once you've done that, you probably won't be using /dev/ttyACM, you'll be using it as a generic USB networking device.

---

### Post by techbrainless on 2011-12-01
Thanks VeeDubb for your reply,

I want to use my phone as gsm modem and configure it with kannel.(not for internet)

---

