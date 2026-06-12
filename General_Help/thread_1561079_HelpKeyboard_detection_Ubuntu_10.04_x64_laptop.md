---
title: "Help:Keyboard detection Ubuntu 10.04 x64 laptop"
date: 2010-08-25
forum: General Help
---

### Post by ngrieb on 2010-08-25
I have an old computer which is slowly dying which has a ps/2 keyboard. I bought an adapter for ps/2 -> usb so that I might be able to adapt it and plug it into the laptop. I have tried to plug it into both the Linux laptop and a Windows Vista laptop. If I do an lsusb the keyboard seems show up in Linux and I think the same was true in Vista, but I cannot find any option to change from the laptop keyboards to an external keyboard. So now the question is is the adapter I bought the wrong kind, is this simply a power issue, or is there a different way to make this work that I don't know about?

---

### Post by davidmohammed on 2010-08-25
When you plug in the external keyboard, are you saying that the keyboard doesnt work?  Does the external keyboard work under vista? 

Immediately after you have plugged in the keyboard, type in a terminal session

dmesg

the last few lines will give a trace of what the kernel thinks it is seeing as a usb device.  Can you post that in a reply?

Also post the results of

lsusb

---

### Post by Capt_Scribble on 2010-08-25
Did you check the BIOS for any settings or options?

---

### Post by ngrieb on 2010-08-26
The first thing I did was check the BIOS, but there were no USB device settings disabled on the laptop. I tried on the Vista laptop, but I also couldn't get it to plug and play there. I'm not quite sure it detected in either case. I don't have access to the laptop right now, but I will get back with answers this weekend. Thanks for the replies.

lsusb gives:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:c211 Suyin Corp.
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It is not showing up here at all now that I have a second look, but the keyboard is also not being powered either. Which is most likely the major problem here. I did make sure to plug it into the powered USB port, but nothing ever seems to happen.

dmesg doesn't give me anything that is related to my keyboard obviously either.

Looks like the adapter I got doesn't work for keyboards as it doesn't work with the desktop either if plugged through the adapter ... so I think I'm SOL on this keayboard...time for a real USB one.    =-(

Thanks anyway for the attempted help.

---

