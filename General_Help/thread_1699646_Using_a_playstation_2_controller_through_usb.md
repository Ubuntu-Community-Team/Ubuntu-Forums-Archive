---
title: "Using a playstation 2 controller through usb"
date: 2011-03-04
forum: General Help
---

### Post by onecircles on 2011-03-04
Problem description: I'm trying to use a playstation 2 dual shock 2  through a USB adapter. In windows it works without any trouble, but in  ubuntu I can't get it to register with the operating system.

Attempted fixes: I have done several fixes off the internet. I've  downloaded the standard joystick stuff from the ubuntu software center.  I've read a lot about it on the internet. Other people who try to use  ps2 gamepads with linux have the same problems, but I haven't been able  to find a fix.

if I cd to /dev/input i'm finding that there is no entry for joystick or js0 or anything like that.
I ran a script yesterday to install joystick support, but I guess it didn't work? 
In input I do have mice, mouse0 mouse1 and mouse2. I read somewhere that  it might be mis-interpreting it as a mouse, I don't know.



The joystick is currently plugged into a usb hub.


from here
[http://www.ubuntugeek.com/how-to-se...-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-set-up-a-gameportgamepad-or-joystick-in-ubuntu.html")
"In a terminal, type the following command
lsmod
It should display a list of the currently loaded modules.
One of the lines should begin with ‘gamepad’
gameport 17160 2 snd_es1938
If you didn’t find any similar line, look for the way to enable the gameport for your specific sound card in the list below."

When I use lsmod, no line begins with "gamepad"

This is old, my sound card doesn't have a game port! OH GOD SO OLD!



can't get this to work either
[http://www.flightgear.org/forums/vi...php?f=11&t=5632]("http://www.flightgear.org/forums/viewtopic.php?f=11&t=5632")



Operating system: Ubuntu Meerkat

System specs: it's a CR-48 Netbook.
Processor: Intel Atom Processor N455 1.66GHz 512K Cache

Chipset: Intel CG82NM10 PCH

Motherboard: Tripod Motherboard MARIO – 6050A240910 – MB – A03

Ram: Hynix 2GB DDR3 1Rx8 PC3 – 10600S Ram

Read Only Memory: ITE IT8500E Flash ROM

SSD Drive: SanDisk sdsa4dh-016G 16GB SATA SSD

Wireless Wan: Qualcomm Gobi2000 PCI Express Mini Card

3g Adapter: AzureWave 802.11 a/b/g/n PCI-E Half MiniCard

Bluetooth: Atheros AR5BBU12 Bluetooth V2.1 EDR

---

