---
title: "I think avaya.jp drivers killed my kppp usb connection /dev/ttyACM0"
date: 2010-03-23
forum: General Help
---

### Post by Elludium_Q-36 on 2010-03-23
I got the system with a couple Epson printers that weren't covered by CUPS but the electronics reclaimer told me they loaded the avaya drivers from [http://avaya.jp](http://avaya.jp)

I had been using a usb phone modem fine for a while, a Motorola iDEN unit on /dev/ttyACM0

I might have had to do ```
 sudo modprobe cdc-acm 
``` possibly ```
sudo mknod /dev/ttyACM0 c 166 0
```

And a modprobe command with the manufacturer's "0x????" code and the product code (I think is was as 044* & 0200 for the phone). (I have it at home but now I'm on "sneaker net ;o? "

I've tried various commands but the closest I get is wvdial recognizing ttyACM0 but not being able to access and when I "mknod" 
the ls command will "see" /dev/ttyACM0 whether or not the phone is plugged via USB.  Bluetooth is not an option and this is the ONLY way I can currently connect this desktop.

I'm aware of cradlepoint but it's not in the budget...

lsusb won't see the Motorola iDEN modem now.

When I plug in the phone, the display stays lit and not for a few seconds after.

I'm going to bring knet back via "sneaker net" / flashdrive and hope I have what I need for dependencies...

I'll gather more info, kernel, etc...  Subscribe to the thread if you are interested in helping or just interested.

I have certainly removed the two avaya packages.

---

### Post by Elludium_Q-36 on 2010-04-24
I'm sure of it now!  But I believe it reflashed an eeprom or the like, in the phone.  I tried to get other systems to recognize the phone via USB and no dice.

I got a new Motorola i290 and it was business as usual!!!
Right back on /dev/ttyACM0 and the problem happened when I tried to use the Avaya.jp drivers to set up an Epson printer.  The driver packages had been there but as soon as I attached and started setting up/testing the printer, while the phone was attached, WHAMMO!!!

I recall seeing a post about Epson commercial driers causing problems and should have erred on the side of caution.

Thing is that part of the Linux lore is that HP and Epson printers are the best supported.

My advice would be to avoid Avaya  like the plague

---

