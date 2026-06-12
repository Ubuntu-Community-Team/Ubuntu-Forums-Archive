---
title: "Weird output from an RFID scanner"
date: 2010-06-10
forum: General Help
---

### Post by Valid Username on 2010-06-10
Hello,

I've just installed Ubuntu 10.04 NetBook Edition (I have the same problem with the Desktop Edition) on an ASUS EeePC S101. I plug a Springcard Prox'n'roll USB RFID scanner <[http://www.springcard.com/products/proxnroll-rfid-scan.html](http://www.springcard.com/products/proxnroll-rfid-scan.html)>.

On another EeePC with an older version of Ubuntu (but that wasn't mine), an Apple MacBook and a PC with Windows XP the scanner works. I only plug the scanner, open a text editor, put a RFID card on the scanner and the card's RFID card is "typed" in the window. ie, on the PowerBook where I'm typing this post: "00000000a0d20e32" (the text between quotes is the TAG that appears when I put a card on the scanner). This without installing any driver. Just plug the scanner on un USB port.

With the last Ubuntu version, I only get some 3 or 4 letters in the text window when I do the same thing.

The scanner seem to be correctly detected on the USB port (here, output of "lsusb" show the scanner as "Bus 002 Device 003: ID 1c34:7241"):

```
-----
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1c34:7241  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b036 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
-----
```
It seem to be mapped to a keybord. When I plug the scanner, /var/log/messages shows :

```
-----
Jun  7 11:29:42 GSN-EeePC-08 kernel: [ 4791.576111] usb 2-2: new full speed USB device using uhci_hcd and address 3
Jun  7 11:29:42 GSN-EeePC-08 kernel: [ 4791.741505] usb 2-2: configuration #1 chosen from 1 choice
Jun  7 11:29:42 GSN-EeePC-08 kernel: [ 4791.753210] input: SpringCard Prox'N'Roll RFID Scanner as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input12
Jun  7 11:29:42 GSN-EeePC-08 kernel: [ 4791.754131] generic-usb 0003:1C34:7241.0002: input,hidraw0: USB HID v1.11 Keyboard [SpringCard Prox'N'Roll RFID Scanner] on usb-0000:00:1d.0-2/input0
-----
```

Does anybody now how to configure Ubuntu in order to have the RFID tag be correctly output?

---

### Post by dino99 on 2010-06-10
into a terminal, try:

sudo update-pciids && update-usbids

and you might need to install rfdump with synaptic

---

### Post by Valid Username on 2010-06-10
> **dino99 said:**
> into a terminal, try:

sudo update-pciids && update-usbids

I've done that (and applyed all Ubutnu available updates) but the result is the same.

> and you might need to install rfdump with synaptic

rfdump should not be necessary. When correctly configured, the reader should be considered as an USB keyboard and when a RFID card is put on the scanner, the scanner is configured to directly output the RFID tag as if it where typed on the keyboard.

---

### Post by Valid Username on 2010-07-19
rfdump  can't connect to the RFID scanner as it is showing as a USB HID keyboard and not a serial port. Any ideas to help me to configure Ubuntu to correctly accept data from this scanner?

---

### Post by Valid Username on 2010-07-21
I finally found what was happening and it's not cool.

Actually the data that appears when a card is presented to the RFID scanner depends on the state of the real keyboard of the EeePC S101. If the "Num Lock" key is locked, the data are correct, if it is unlocked, it data are not correct. The locking/unlocking of the "Num Lock" key changes the way data coming from the RFID reader are interpreted. The player is not treated as a keyboard independent of the keyboard of the laptop :-( 

Is it possible to ensure that the reader be treated as keyboard independent from the laptop's keyboard? If so how?

---

### Post by Valid Username on 2010-07-21
I tryed to connect a real external USB Keyboard and I have the same problem. The "Num Lock" key of the notepad's keyboard change the status of the external keyboard. Does someone know of a mean to have the external and internal keyboad works independently?

---

### Post by Valid Username on 2010-07-21
I installed numlockx, followed instruction from [http://ubuntuguide.net/enable-number-pad-numlock-at-startup-in-ubuntu-login-window]("http://ubuntuguide.net/enable-number-pad-numlock-at-startup-in-ubuntu-login-window") and now I can use the RFID scanner and the netbook keyboard. Caution, add the numlockx instructions just before the end of the config file as stated in the instructions above!

---

