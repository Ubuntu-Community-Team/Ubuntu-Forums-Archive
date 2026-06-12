---
title: "another ubuntu 9.10 problem with packages and unability to install"
date: 2010-04-28
forum: General Help
---

### Post by mitraljez on 2010-04-28
So I recently switched from Win xp sp3 to ubuntu 9.10.

the problem is I cant get to connect to internet (via mobile phone USB modem since there's no other way of connection online available).The OS doesnt recognise the phone, therefore I cant connect (Im pretty sure I got all the settings in Network managing correct, since I didnt have to change much).

I downloaded wdial and launch2net for ubuntu, but its impossible to install without internet, and I constantly get Dependencies error and its impossible to fix :(

so, how do I get the ubuntu to recognize my mobile phone via USB cable, without the use of internet to download drivers which are pain in the *** to install?

---

### Post by dino99 on 2010-04-28
if you want help you need to give us the exact config and you should use packages from synaptic: 

- wdial is not an ubuntu package: there is wvdial
- cant find your launch2net, not an ubuntu package

so where i've you got these packages ?
if you have installed 9.10 you need to use packages only from it

Why have you not installed 10.04 which brings more hardware supports ?

googling around launch2net, i've found this howto:

[http://www.ubuntugeek.com/launch2net-mobile-internet-connection-manager-for-ubuntu.html](http://www.ubuntugeek.com/launch2net-mobile-internet-connection-manager-for-ubuntu.html)
have you followed the same rules ?

---

### Post by klemes on 2010-04-28
What type of cell phone/modem are you using?
You could try unplugging it & plugging it back in and see dmesg|tail -f to see if it correctly recognized as a modem.Also some modems have the option when you plug them in the USB to be recognized as a mass storage device(ie card reader for their flash card) or initialize a data connection to be used as modem or sync over USB cable.You must choose the later.
Last if you had a Bluetooth USB dongle or if it is a netbook with built-in bluetooth adapter you would achieve more easily connectivity as a modem,given  that your phone supports the correct bluetooth DUN profile.:guitar:

---

