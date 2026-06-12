---
title: "USB keyboard fails in Jaunty - please help!"
date: 2009-07-14
forum: General Help
---

### Post by hyperyoda on 2009-07-14
Just installed Ubuntu 9.04 and my USB keyboard is not recognized. It works fine in Microsoft Windows Vista. I think it is an issue with newer kernels because I also tried it with Debian 5.01 and same problem (keyboard's green status light never comes on - even during entire boot process as it normally would). 

I really want to use this and not my junky 10 year old PS/2 keyboard so I'd really appreciate *any* help.

Here is the keyboard info:

Logitech Deluxe 250 Keyboard
M/N: Y-UL76
P/N: 867675-0403
PID: BT909DF1068

Here is a link to it: [http://www.amazon.com/Logitech-967738-0403-Deluxe-Qualified-Keyboard/dp/B000I4WHD6]("http://www.amazon.com/Logitech-967738-0403-Deluxe-Qualified-Keyboard/dp/B000I4WHD6")

Zach

---

### Post by NightwishFan on 2009-07-14
Open up the system log for me, it is under the System - Admin menu.

When you plug in your keyboard, does anything appear in the 'messages' log?

(You do not have to reboot if it is usb, just take the device out and back in.)

---

### Post by hyperyoda on 2009-07-17
> **NightwishFan said:**
> Open up the system log for me, it is under the System - Admin menu.

When you plug in your keyboard, does anything appear in the 'messages' log?

(You do not have to reboot if it is usb, just take the device out and back in.)

Here is what shows up in the log:

ul 17 00:45:25 hyperyoda kernel: [241558.416026] usb 6-1: new low speed USB device using ohci_hcd and address 2
Jul 17 00:45:25 hyperyoda kernel: [241558.590491] usb 6-1: configuration #1 chosen from 1 choice
Jul 17 00:45:25 hyperyoda kernel: [241558.645010] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/input/input8
Jul 17 00:45:25 hyperyoda kernel: [241558.656662] generic-usb 0003:046D:C312.0004: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:13.1-1/input0
Jul 17 00:45:25 hyperyoda kernel: [241558.672122] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.1/input/input9
Jul 17 00:45:25 hyperyoda kernel: [241558.693021] generic-usb 0003:046D:C312.0005: input,hiddev96,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:13.1-1/input1

I installed the driver from [www.hidpoint.com](www.hidpoint.com) but it didn't work because my keyboard was not in the list of keyboard models it let you select :( 

Here is my keyboard:
[http://www.amazon.com/Logitech-967973-0403-Internet-Desktop-Keyboard/dp/B000HJOUP0/ref=sr_1_2?ie=UTF8&qid=1247806041&sr=1-2](http://www.amazon.com/Logitech-967973-0403-Internet-Desktop-Keyboard/dp/B000HJOUP0/ref=sr_1_2?ie=UTF8&qid=1247806041&sr=1-2)

---

### Post by NightwishFan on 2009-07-17
The log shows no problems and it seems to recognize the device. I have little experience in this matter, though I suggest perhaps search for a problem with the device. I will try as well.

---

### Post by hyperyoda on 2009-07-17
> **NightwishFan said:**
> The log shows no problems and it seems to recognize the device. I have little experience in this matter, though I suggest perhaps search for a problem with the device. I will try as well.

As I said the "problem" is that the keyboard is unresponsive!

---

### Post by NightwishFan on 2009-07-17
I am quite aware. :)

The log shows no problems however. Which would have helped a good bit if it did. Do other USB devices work? It might be a bios issue if not. (Though I doubt it).

---

### Post by hyperyoda on 2009-07-19
> **NightwishFan said:**
> I am quite aware. :)

The log shows no problems however. Which would have helped a good bit if it did. Do other USB devices work? It might be a bios issue if not. (Though I doubt it).

Ah. Yeah my USb mouse works.

---

### Post by NightwishFan on 2009-07-20
See if it works using a live cd of an earlier version of Ubuntu if possible. Odd hardware problems exist using some kernels.

---

### Post by DrMelon on 2009-07-22
I'm in the same situation, except it's my USB Mouse that is the problem. It worked just fine in 8.10, but since I updated today it no longer responds. The logs do not indicate any kind of error, and detect it just fine.

---

