---
title: "Logitech Wireless Touchpad with Multi-Touch"
date: 2012-06-19
forum: General Help
---

### Post by Welly Wu on 2012-06-19
[http://www.logitech.com/en-us/mice-pointers/mice/8417](http://www.logitech.com/en-us/mice-pointers/mice/8417)

[http://www.amazon.com/gp/product/B005DSPLC6/ref=ox_sc_act_title_1?ie=UTF8&m=ATVPDKIKX0DER](http://www.amazon.com/gp/product/B005DSPLC6/ref=ox_sc_act_title_1?ie=UTF8&m=ATVPDKIKX0DER)

I have an ASUS N61JV-X2 notebook PC with Crucial 8 GB DDR3 1,066 MHz PC-8500 SODIMM SDRAM and an Intel 2nd Generation 2.5" MLC NAND FLASH X25-M 160 GB Solid State Drive running Ubuntu 12.04 64 bit Long Term Support.

I am keenly interested in purchasing this Logitech Wireless Touchpad with Multi-Touch Navigation. According to the Amazon reviews, it is compatible with Ubuntu 11.10 32 and 64 bit. It comes with its own Logitech USB 2.0 Unifying Receiver.

Does anyone else here have it? If so, then can you tell me if it will work with Ubuntu 12.04 64 bit LTS? How well does it perform?

I am looking for an alternative pointing device. I have an ASUS Bluetooth Laser Mouse and it is alright, but I want something that is different. This looks like it might do the job. What I am trying to do is to reduce repetitive motions by using my mouse to reduce strain on my right arm and shoulder. I use my computer a lot and I do not feel tired or discomfort when I use my track pad on my ASUS N61JV-X2 notebook PC, but it is too small. I need a much bigger track pad surface that I can move around and position on my desk.

I prefer using a track pad compared to a mouse and this seems to be the only product available to PC users that looks to be compatible with Ubuntu GNU/Linux users as well.

What do you think?

Should I get it or not?

I plan to make my purchase tomorrow morning.

---

### Post by Welly Wu on 2012-06-23
I received the safe delivery of my Logitech Wireless Touchpad today from Amazon. I plugged in the Logitech Unifying Receiver into a Super Speed USB 3.0 port and I put in two fresh AA alkaline batteries into the Logitech Wireless Touchpad and I switched it on. It works right out of the box with Ubuntu 12.04 64 bit Long Term Support. I can perform one, two, three, and four finger gestures and events. I can tap on the surface and it will act as a left mouse button click. There are two separate mouse buttons located on the bottom. It is pretty big and chunky. I have an IKEA desk with a glass surface and it stays put on my desk without slipping or sliding. In terms of performance, it is pretty accurate and precise. Using it to execute multiple gestures and events is solid with no problems. Scrolling vertically and horizontally is very fluid and smooth. I have no pain or discomfort while using my Logitech Wireless Touchpad whatsoever. I also have an ASUS Bluetooth laser mouse and it does cause pain and discomfort after 10 minutes of usage and it is an ergonomic mouse. It is an ASUS BX700 Bluetooth laser mouse. I stopped using it.

There are two websites on the Internet that have detailed instructions and documentation on how to customize the Logitech Wireless Touchpad so that I can associate key combinations with specific gestures to trigger specific events. As it stands right now, it is almost perfect right out of the box. I just need to add four finger swipes to the left, right, and bottom to trigger the Super, Alt, and minimize window events and it will be perfect to use with Unity 3D desktop environment. I think that I will carefully read those websites and the documentation and I will get to work on it later tonight.

I like my Logitech Wireless Touchpad quite a bit. I only paid $25.00 USD for a used one from Amazon which is quite cheap. When it arrived at my home, it was packaged as if it were brand new.

I recommend it to other users especially if you use Ubuntu 12.04 64 bit Long Term Support. I will do a follow up post to detail my custom configuration after I test to ensure that it works just in case someone else might want to learn how to do it for their own Logitech Wireless Touchpad.

---

### Post by Welly Wu on 2012-06-23
This is my /usr/lib/udev/keymaps/logitech-touchpad custom file:

0x700E2 leftalt #Four up 1
0x7002B tab #Four up 2
0x700E3 left #Four down 1
0x700007 left #Four down 2
0x700E3 rightalt #Four right 1
0x7004F rightalt #Four right 2
0x700E3 leftmeta #Four left 1
0x70050 leftmeta #Four left 2

I configured it to make these custom gestures and events permanent:

If you want to make that change permanent, you need to add an udev rule to /lib/udev/rules.d/95-keymap.rules that applies the keymap file to the device.

Open the file: gksudo gedit /lib/udev/rules.d/95-keymap.rules
At the bottom of the file, but before the LABEL="keyboard_end" line, add:

ENV{ID_VENDOR}=="Logitech*", ATTRS{idProduct}=="c52d", RUN+="keymap $name logitech-touchpad"

Here are my resources:

1. [http://norgelinux.blogspot.com/2012/02/logitech-wireless-touchpad.html](http://norgelinux.blogspot.com/2012/02/logitech-wireless-touchpad.html)

2. [http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter](http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter)

---

### Post by Welly Wu on 2012-06-24
I don't know if anyone else here can help me with these specific problems, but I will give it a try.

1. My custom logitech-touchpad file will not load after a cold boot or re-boot. Thus, four finger gestures to the left, right, and down do not trigger any events. I must manually load my custom logitech-touchpad file by typing in sudo /lib/udev/keymap /dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse /lib/udev/keymaps/logitech-touchpad. Sometimes, this does not work properly and I get an error message stating that /lib//udev/keymaps/logitech-touchpad could not be found.

2. Four finger sweeps downward do not trigger any events. I tried the specific codes:

0x700E3 leftmeta #Four down 1
0x70007 W #Four Down 2

to trigger the Super + W key combination, but it does not work. In fact, when I input this into my logitech-touchpad file, then four finger sweeps to the right no longer trigger the Heads Up Display anymore. I noticed that 0x700E3 is used for the first part of Four Finger Sweep to the right too. I tried to comment out both the Four Finger sweep Downward in my logitech-touchpad, but Four Finger sweep to the right no longer triggers the Heads Up Display again.

How do I determine the specific codes used for Four Finger sweep Down in Ubuntu?

So far, I like the Logitech Wireless Touchpad as it eliminates strain, pain, and discomfort compared to using my ASUS BX700 Bluetooth laser mouse.

Can anyone else help me?

---

### Post by Welly Wu on 2012-07-10
sudo /lib/udev/keymap /dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse /lib/udev/keymaps/logitech-touchpad

---

### Post by ionospheric on 2012-07-25
you could a script to autostart containing this command.
I've had problems doing this until I added "sh" in front of the command:

contents of script file:
```

#!/bin/bash

sh xinput (etc.)

```

---

### Post by adityakoparkar on 2013-02-05
Hello,
so finally were you able to get the four and three finger swipe to work?
Coz I am planning to buy one of these for my ubuntu box and wanted to be sure if it worked.

---

