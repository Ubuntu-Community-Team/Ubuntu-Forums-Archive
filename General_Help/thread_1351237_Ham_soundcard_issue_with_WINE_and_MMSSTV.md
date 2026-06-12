---
title: "Ham soundcard issue with WINE and MMSSTV"
date: 2009-12-10
forum: General Help
---

### Post by WU8V on 2009-12-10
I am an amateur radio operator, and I have been trying to totally abandon windoze operating system. However, I have a couple of programs that I really like to use that I need WINE support for. I have the programs loaded and they seem to be working ok with the exception of the sound card(s) selection features.

I am currently running Karmic.

The problem is that I can not get some of my win based programs to find their respective sound cards using the wine interface

List of cards: 
1) Intel onboard sound card that I would like to eventually use for Echolink 

2)Soundblaster that I would like to handle all the regular system sounds and MP3s and videos and such. Non ham related stuff, and for the most part Linux driven.
 
3) Signalink USB sound card and radio interface. This is the main one that I want to work well, as it will be for Digipan (win based) and MMSSTV (also win based) I can use FLDigi for the psk31 duties but I like DigiPan better, and the Qsstv looks weak compared to MMSSTV. 

Echolink is a low priority, and I have another program that I can use for the PSK, so I would like to start by getting the MMSSTV program working with the Signalink USB

I can start the MMSSTV program and when I try to select a sound card, I have a list of  -1, 0, 1, 2, and 3
Any of the cards that I select ALL go to the onboard soundcard (intel) except when I select 3it tells me that it cannot find soundcard 3.

**[COLOR="Red"]How can I get wine to allow the MMSSTV program to choose the USB device?[/COLOR]**

Any suggestions to sort this mess out would be greatly appreciated

---

### Post by WU8V on 2009-12-11
Just to update, and ask another question...

I went into pulse volume control, and "turned off" both the internal and the sound blaster sound cards, and now the USB interface is accepting all the sound for the system. 

But when I turn the others back on, they will not accept th eother sound cards to take the sounds from the linux based programs and the system sounds...

**[COLOR="Red"]Is there a way to permanently tell the system what applications use which soundcards??? [/COLOR]**

Thanks and regards,

---

### Post by kd5mkv on 2010-07-05
I have you tried finding what USB port your hardware is under. Under terminal $dmesg   it list all kinds of hardware on your machine for expample: 19.006314] usb 3-2: FTDI USB Serial Device converter now attached to ttyUSB0
[   19.006348] usbcore: registered new interface driver ftdi_sio
The above FTDI device above is my Kiss Tnc and it is on /dev/ttyUSB0 you must use the exact ttyUSB, MMSSTV works fine on Ubuntu, I am using Wine 1.2 and have Airmail,MMsstv working fairly well.Steve kd5mkv

---

### Post by kd5mkv on 2010-08-02
One problem, Ubuntu changed something on 9.10, I ve tried Gnome Alsamixer from synaptic to control the audio settings. Also I
have found the version of Wine 1.2 works,So if you can get audio to and fro, does USB device working with equipment? Steve KD5MKV

---

