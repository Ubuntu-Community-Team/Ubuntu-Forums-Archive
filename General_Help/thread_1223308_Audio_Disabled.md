---
title: "Audio Disabled?"
date: 2009-07-26
forum: General Help
---

### Post by This Stench Craves my Pen on 2009-07-26
Hey guys I have virtually no knowledge of Ubuntu and this is my first post so dum down your responses if at all possible..

Everything was fine till I started messing with some terminal commands trying to install WINE I was using tutorials here and on the wine site.. my sound appears to have disabled itself? I don't understand the problem here but my control for sound on the upper bar has vanished and I can't hear anything. Any help is appreciated, thanks..

not sure if this helps but here is some system info.

Ubuntu 
Release 9.04 (jaunty)
Kernel Linux 2.6.28-13-generic
GNOME 2.26.1

Hardware
Memory: 495.9 MiB
Processor: Intel(R) Pentium(R) 4 CPhttp://mail.live.com/default.aspx?wa=wsignin1.0U 2.80GHz

System Status
Available Disk Space: 30.7 GiB

---

### Post by Ravernomina on 2009-07-26
try going to system>administration>sounds. Change every option to ALSA (advanced Linux Sounds architecture) Then try to test every one. After that go to the sound icon in the top near the shutdown,restart, ect and turn the volume all the way up.


Report back ill keep an eye on this post


Btw welcome to ubuntu and welcome to Linux :) you will be happy here :)


Btw to make life easy on u try learning some terminal commands on google ;)

---

### Post by This Stench Craves my Pen on 2009-07-26
> **Ravernomina said:**
> try going to system>preferences>sounds. Change every option to ALSA (advanced Linux Sounds architecture) Then try to test every one. After that go to the sound icon in the top near the shutdown,restart, ect and turn the volume all the way up.


Report back ill keep an eye on this post


Btw welcome to ubuntu and welcome to Linux :) you will be happy here :)


Btw to make life easy on u try learning some terminal commands on google ;)

Thanks... Hmm.. I can't find "Preferences" under system or anything else sure its called that?

---

### Post by Ravernomina on 2009-07-26
o sorry i fail its it in administration.... im sorry XD

---

### Post by This Stench Craves my Pen on 2009-07-26
Ok.. cool.. bare with me here.. how  do I get to administration? it's not exactly listed here

---

### Post by Ravernomina on 2009-07-26
here let me get into ubuntu and help you


Right now im on Mac OS X so 1 sec :)

---

### Post by darolu on 2009-07-26
He means the top bar (panel), you should have System on the far left corner, next to Apps and Places.

Anyways, open a terminal and do:
```
cat /proc/asound/cards
```
Make sure your audio card is there, if not, paste whatever it listed here.

If your card is there do:
```
alsamixer
```
and play with your channels, make sure the master one isn't muted, if you have an analog+digital output soundcard ensure you have the right output set.

---

### Post by Ravernomina on 2009-07-26
alright on ubuntu well ive been on for 20 secs.... now go to the top you will see the word "system" click on it. Then put ur pointer on preferences. On thats menu that comes up look for the word "sound" then click. A window will pop up now ware everything says Autodect, Change to ALSA (advanced Linux sound architecture) then hit the button "test"

---

### Post by This Stench Craves my Pen on 2009-07-26
Yeah I got that much... I went there it isn't listed

and I got this

0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1981B at irq 17

I went and turned it all up no sound

---

### Post by This Stench Craves my Pen on 2009-07-26
Ok apparently this error was a new  development considering you guys stopped suggesting things.. I download something called PulseAudio Volume Control and it was something was muted somehow  and for some reason I didn't have preferences under system downloaded this tool un-muted can hear stuff now. Maybe my topic will help some others.

---

