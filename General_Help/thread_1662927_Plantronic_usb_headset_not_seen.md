---
title: "Plantronic usb headset not seen"
date: 2011-01-08
forum: General Help
---

### Post by Qazulight on 2011-01-08
I just got my fresh install of the Ubuntu 64 bit running on my new build system. Fresh, clean, new.

Got Google Earth working, got Evolution sending and receiving, got the plugi-in I want for Firefox running. Found my network printer and it is printing. I am feeling pretty good. Didn't get a real good start until 10;30 this morning. and it is now only 8:45. Cool.

The last thing I need to get running is the Plantronics Gigaware usb headset. I can open the sound icon at the top of the screen and by selecting "Audio adapter - 1 output/1 input - digital stereo (iec958) + analog mono input" I can get a sound when I run the test, but there is no sound from the Flash content on the websites.

I suspect that I need to get the system to acknowledge the headset is there. I have tried plugging in the headset and rebooting to no avail. I tried going into the BIOS and disabling the on board sound card. That did not seem to help either. 

I read some of the threads about the audio and I downloaded AlsaPlayer, but that did not help.

This seems to be a continuing problem. I am about ready to throw money at it and go buy a different headset.

Ideas?

Cheers
Qazulight

---

### Post by Bucky Ball on 2011-01-08
Welcome. 

Open a terminal (Applications >Accessories >Terminal) and type this in:

```
lsusb
```Is the headset there in the output? Should show 'Plantronics USB Headset' or the model or something. Best to make sure the system knows it's there first. ;)'

---

### Post by vidtek on 2011-01-08
> **Qazulight said:**
> I just got my fresh install of the Ubuntu 64 bit running on my new build system. Fresh, clean, new.

Got Google Earth working, got Evolution sending and receiving, got the plugi-in I want for Firefox running. Found my network printer and it is printing. I am feeling pretty good. Didn't get a real good start until 10;30 this morning. and it is now only 8:45. Cool.

The last thing I need to get running is the Plantronics Gigaware usb headset. I can open the sound icon at the top of the screen and by selecting "Audio adapter - 1 output/1 input - digital stereo (iec958) + analog mono input" I can get a sound when I run the test, but there is no sound from the Flash content on the websites.

I suspect that I need to get the system to acknowledge the headset is there. I have tried plugging in the headset and rebooting to no avail. I tried going into the BIOS and disabling the on board sound card. That did not seem to help either. 

I read some of the threads about the audio and I downloaded AlsaPlayer, but that did not help.

This seems to be a continuing problem. I am about ready to throw money at it and go buy a different headset.

Ideas?

Cheers
Qazulight

I have a plantronics usb headset that I use occasionally.  It's an SRS usb adaptor with sockets for the headset mic and earphones at the back.  If this is similar to yours, don't give up yet, you'll only have the same problems with a replacement.

My plantronics adaptor come up as a C-Media device as:

```
lsusb
Bus 006 Device 004: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
```I only use it occasionally and it is a real pain because I always forget what I did before to enable it!

Install pulse audio, alsa and any other mixers you can find and go through the settings, that's what I did.

btw, I'm using meercat 64-bit and KDE4

best of luck Tony

---

### Post by Qazulight on 2011-01-08
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 002: ID 06a3:8020 Saitek PLC 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It looks like it sees the headset I found my keyboard and mouse no problem, but they are enabled in the BIOS. 

C-Media Electronics Audio Adapter is not in my list when I open the sound preferences.

Thanks
Qazulight.

---

### Post by vidtek on 2011-01-17
> **Qazulight said:**
> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 002: ID 06a3:8020 Saitek PLC 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It looks like it sees the headset I found my keyboard and mouse no problem, but they are enabled in the BIOS. 

C-Media Electronics Audio Adapter is not in my list when I open the sound preferences.

Thanks
Qazulight.

OK. Looks like it's found your headset, bus2, device 003 C-Media.


I played with mine on the week-end and the enabling setting is in the pulse audio mixer.

I'm doing this at the office so I'm trying to remember how it went.

You need to set the configuration hardware to the headset in the far right tab in pulse audio mixer, this disables the normal analogue or digital output. It's a radio button choice.

Then just go through the playback devices tab and set levels.

It should work now, mine did. When I want to revert back to my optical output I just yank the USB adaptor and it goes back automatically.

Best regards, Tony.

---

