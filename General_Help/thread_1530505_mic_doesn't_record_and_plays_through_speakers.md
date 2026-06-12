---
title: "mic doesn't record and plays through speakers"
date: 2010-07-13
forum: General Help
---

### Post by laerub18 on 2010-07-13
hey,
here's my problem:

i have a sony vaio vgn-n38z laptop with an external microphone which i'm trying to use with skype. the microphone (which works; i tried it on another computer) doesn't record anything, but when i speak in it, it actually plays through the speakers (kind of like karaoke).

so basically, i want it to stop playing through the speakers and start recording!

with lspci: my Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

with the command: head -n 1 /proc/asound/card0/codec*, i get:
Codec: Realtek ALC262

thanks!

---

### Post by laerub18 on 2010-07-15
bump

---

### Post by laerub18 on 2010-07-19
anyone ?

---

### Post by CoolJohnB on 2010-07-19
You could try this thread: [http://ubuntuforums.org/showthread.php?t=1466096](http://ubuntuforums.org/showthread.php?t=1466096)

It worked for me on my Dell laptop, hope it works for you.

---

### Post by laerub18 on 2010-07-19
i tried it but i sitll have the problem!

---

### Post by laerub18 on 2010-07-23
anyone ?

---

### Post by lidex on 2010-07-24
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

Also use pulseaudio volume control, the 'Input Devices' tab. In the 'Show' dropdown selector select 'Monitors'. Now mute or reduce levels.

---

### Post by laerub18 on 2010-07-24
**Gnome-alsamixer**
ok

**Use 'Edit -> Sound Card Properties' menu to enable elements.**
ok; they're all already enabled
[ATTACH]164403[/ATTACH]

**sudo apt-get install gnome-alsamixer**
its already installed

**pavucontrol:**
already unmuted :)
[ATTACH]164400[/ATTACH]

**sound preferences:**
same here
[ATTACH]164401[/ATTACH]

**A****lso use pulseaudio volume control, the 'Input Devices' tab. In the 'Show' dropdown selector select 'Monitors'. Now mute or reduce levels.**
ok i did that, it didn't change anything

also:
[ATTACH]164402[/ATTACH]


sorry but i still can't record any sound and can hear my self in the speakers.. :(

---

### Post by lidex on 2010-07-24
The first screen is not Sound Card Properties. Back in the volume control, try backing the level for right channel all the way down.

---

### Post by laerub18 on 2010-07-25
oops you're right.. here is sound card properties:
[ATTACH]164489[/ATTACH]

**Back in the volume control, try backing the level for right channel all the way down.**
like this ?
[ATTACH]164491[/ATTACH]

also if it can help:
[ATTACH]164490[/ATTACH]

other wise no , still not working.. maybe its something to do with the driver. are there others i can try?

---

### Post by lidex on 2010-07-25
oops

---

### Post by brigit on 2010-10-11
I'm having a very similer problem, although I can get rid of hearing my self through the speakers if I take the capture of the mic. However I like it cause it tells me the mic IS working, so its software problem.
I'm running Kubuntu Lucid on a Acer Travelmate c300 (or c302xmi). 
The mic used to work, pre upgrade to lucid, however I duel boot with karmic and its stopped working there too since an upgrade.
I've had this problem for 3? months, and have been trying most of the tips I can find. 
Mic is not muted (i can hear it), mic boost is on, the correct mic is selected.
Any help Please! Half the reason I have a computer is to talk on skype!

---

### Post by lidex on 2010-10-11
> **brigit said:**
> I'm having a very similer problem, although I can get rid of hearing my self through the speakers if I take the capture of the mic. However I like it cause it tells me the mic IS working, so its software problem.
I'm running Kubuntu Lucid on a Acer Travelmate c300 (or c302xmi). 
The mic used to work, pre upgrade to lucid, however I duel boot with karmic and its stopped working there too since an upgrade.
I've had this problem for 3? months, and have been trying most of the tips I can find. 
Mic is not muted (i can hear it), mic boost is on, the correct mic is selected.
Any help Please! Half the reason I have a computer is to talk on skype!
So the mic works, just not in skype?
[http://kubuntuforums.net/forums/index.php?action=search2](http://kubuntuforums.net/forums/index.php?action=search2)

---

