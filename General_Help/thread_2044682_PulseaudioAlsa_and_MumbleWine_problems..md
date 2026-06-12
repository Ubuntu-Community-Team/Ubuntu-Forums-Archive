---
title: "Pulseaudio/Alsa and /MumbleWine problems."
date: 2012-08-19
forum: General Help
---

### Post by Aydos on 2012-08-19
Hello Everyone,

I just returned to using Linux. I am on Ubuntu 12.04 x64.

I installed the stable version of Wine yesterday and set up everything on my system.

I installed League of Legends via PlayOnLinux and it is running fine.

My audio devices are a HDMI monitor and a USB Corsair Vengeance Headset.

My sound comes out of the headset fine when I have it plugged in.

However, when I open Wine the Wine sounds come from the monitor speakers via HDMI.

The only help I could find on the Wine forums was to disable pulse audio and use Alsa.

This gave me sound from Wine so I could hear League of Legends, but now I cannot hear Mumble (Voip client). I can pick different audio devices in Mumble but it shows like 50 for some reason and none seem to work.

Can anyone help me getting pulseaudio to play nice with Wine?

---

### Post by Aydos on 2012-08-20
Bump.

Anyone know how to make Wine play nice wtih pulseaudio?

---

### Post by Aydos on 2012-10-23
I thought it would be easier to resurrect my old thread than start a new one.

This problem also happens with Manger (ventrilo alternative).

Anytime I am running a native Linux VOIP program and a game in WINE the sound will get hijacked just to WINE.

I remember there use to be something called WinePulse you could use to fix the problem, but the project was stopped, because supposedly this is built into WINE now in some way.

Anyone have any problems or any ideas how I can make my VOIP software and games in WINE play nice?

Thank you.

---

### Post by Aydos on 2012-10-23
Shameless Bump

---

### Post by father_ted on 2012-10-25
The pulseaudio version with 12.04 is ancient. The version that comes with the audio ppa for 12.04 fixed almost everything for me. i can listen any audio app native in linux while gaming in wine and it works very well with the very occasional soft 'burp' from time to time. i am using a usb dac so the burping may well be driver related.

if your voip app tries to run at 48k it may glitch a little as wine game audio will be coming at 44.1 and the resampling in pulse is not great - although steadily improving.

[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu)

---

### Post by father_ted on 2012-10-25
FYI

[http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)

---

### Post by Aydos on 2012-11-14
Awesome and Thank You!

What steps do I need to take to make Ubuntu 12.10 install this version of Wine and not the default one?

---

