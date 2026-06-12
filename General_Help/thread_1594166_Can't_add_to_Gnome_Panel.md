---
title: "Can't add to Gnome Panel"
date: 2010-10-12
forum: General Help
---

### Post by Dave M G on 2010-10-12
On my laptop, I have a compltetely fresh install of Ubuntu 10.10.

If I right click the Gnome Panel, the menu that appears only shows two options: "Help" and "About Panels".

There is no option to add anything to the panel.

When I looked on line, every indication seemed to be that there should be more options, including something along the lines of "Add to Panel".

Where has this option gone, and how can I get it to appear?

Thank you for any advice.

---

### Post by sendblink23 on 2010-10-12
> **Dave M G said:**
> On my laptop, I have a compltetely fresh install of Ubuntu 10.10.

If I right click the Gnome Panel, the menu that appears only shows two options: "Help" and "About Panels".

There is no option to add anything to the panel.

When I looked on line, every indication seemed to be that there should be more options, including something along the lines of "Add to Panel".

Where has this option gone, and how can I get it to appear?

Thank you for any advice.

I don't have any ideas for suggestions.. but I will ask on your other computer.. does that it have that issue as well?

---

### Post by Dave M G on 2010-10-12
sendblink23,

Thank you for responding.

No, my other computer, on which I upgraded from 10.04, when I right click on the Gnome Panel, I get a whole set of options, including one to "Add to Panel...".

So the problem would seem to be specific to the laptop and it's settings.

As mentioned, it is a complete fresh install, so I have not done anything to customize or change it yet.

---

### Post by TNT1 on 2010-10-12
Try 
```
rm -r ~/.gconf/apps/panel
```

See if a fresh default panel works?

you either have to logout and back in or kill the panel for the changes to be applied

---

### Post by Dave M G on 2010-10-12
TNT1,

Thank you for the suggestion.

Removing the panel configuration with the command you suggested, then rebooting, has solved the problem.

Your help is much appreciated.

---

### Post by balkce on 2010-10-29
You don't need to erase all of your panel settings to remedy this. I had the same problem, and the issue was that the panel was globally locked down.

To unlock it, I followed the advise from:

[http://ubuntuforums.org/showpost.php?p=5010238&postcount=3](http://ubuntuforums.org/showpost.php?p=5010238&postcount=3)

Basically, you need to either run:

> gconf-editorAnd navigate to  "apps" > "panel" > "global", and uncheck the key called "locked_down".

Or, run:

> gconftool -t bool -s /apps/panel/global/locked_down falseBoth methods do the same thing: globally unlock the panel.

You then need to restart the panel by running:

> killall gnome-panelHope this helps.

---

### Post by jameshoo on 2010-11-21
gconftool -t bool -s /apps/panel/global/locked_down false
 killall gnome-panel
Thank you. This worked for me.:D:D

---

### Post by karthick87 on 2010-11-21
I tried this but it din work for me..I wanna add **StackApplet  **to my panel..I have installed StackApplet but when i add it to my panel nothing appears in my panel.

[[IMG]http://hosting11.imagecross.com/image-hosting-55/3113Screenshot-Add-to-Panel.png[/IMG]](http://www.imagecross.com/)[](http://www.imagecross.com/)

---

### Post by maheshchinna on 2010-11-21
Sound problem in ubuntu 10.10?
hi.yesterday i install ubuntu 10.10 linux in my pc. everything work fine except sound.i have 4.1 creative sound system.the problem is that i heard only front-L&-R speakers only.there is no sound from rear speakers.i like ubuntu but i am a music lover. i installed all required softwares.when i run this command            
 "pavumeter" in run application .it shows all speakers working working fine but i can't get rear speakers.
mahesh@mahesh-M61PME-S2P:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

mahesh@mahesh-M61PME-S2P:~$ aplay -L
default
pulse
Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
Front speakers
surround40:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Digital
IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
Direct sample mixing device
dmix:CARD=NVidia,DEV=1
HDA NVidia, ALC883 Digital
Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
HDA NVidia, ALC883 Digital
Direct sample snooping device
hw:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
HDA NVidia, ALC883 Digital
Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
HDA NVidia, ALC883 Analog
Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
HDA NVidia, ALC883 Digital
Hardware device with all software conversions
......

   mahesh@mahesh-M61PME-S2P:~$ speaker-test -Dplug:surround40 -c4 -l1 -twav

speaker-test 1.0.23

Playback device is plug:surround40
Stream parameters are 48000Hz, S16_LE, 4 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 524288
Period size range from 16 to 262144
Using max buffer size 524288
Periods = 4
was set period_size = 131072
was set buffer_size = 524288
 0 - Front Left
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
Time per period = 11.087757
pu
but i cant hear sound from rear speakers.how to enable rear speakers jack.pulse audio manager shows all speakers working properly.
plz give me replay

---

### Post by Ryan Sparx on 2010-12-22
> **balkce said:**
> You don't need to erase all of your panel settings to remedy this. I had the same problem, and the issue was that the panel was globally locked down.

To unlock it, I followed the advise from:

[http://ubuntuforums.org/showpost.php?p=5010238&postcount=3](http://ubuntuforums.org/showpost.php?p=5010238&postcount=3)

Basically, you need to either run:

And navigate to  "apps" > "panel" > "global", and uncheck the key called "locked_down".

Or, run:

Both methods do the same thing: globally unlock the panel.

You then need to restart the panel by running:

Hope this helps.


u r right :popcorn:

i locked down my panels with "ubuntu tweak" and forgot about that, thnx buddy.

---

