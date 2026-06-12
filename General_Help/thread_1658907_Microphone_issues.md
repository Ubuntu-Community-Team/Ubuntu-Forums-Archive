---
title: "Microphone issues"
date: 2011-01-03
forum: General Help
---

### Post by Lyubo on 2011-01-03
Hey there,

Yesterday I installed Ubuntu 10.04 from the CD I ordered some time ago and everything was ok. Today I upgraded to 11.04 and now my microphone is not working. The microphone was tested in 10.04 and it was working perfectly. Both skype and the in built sound options recognize that a microphone is plugged in but i cannot record anything with the sound recorder.

The machine in Toshiba Satellite L40 - 170 if it matters. Please help

Thanks in advance!

---

### Post by gradinaruvasile on 2011-01-03
The sound system ALSA that takes care of stuff like this.
On top of ALSA there is PulseAudio - this is the sound server that takes the sound streams from ALSA and routes them through itself. And makes managing sound sources easy.
The GUI for configuring the sound devices is PulseAudio's gnome-volume-control (this is launched from the right-click menu).


To test if you have a working mic in PulseAudio, first open the config menu, go to the hardware tab, make sure that your integrated device is set up as "Analog Stereo Duplex".

Then, go to the input tab, select your mic source (you probably have at least 2 input sources, test all) and tap your mic. If you see the sound levels bouncing, PulseAudio can use your mic.
If this is not working, open a terminal and type alsamixer in it, press enter. 
Press tab to go to the "recording" tab and see what you have there. You must have at least one device tagged with "CAPTURE" (red text), the correct input source selected, mic levels up and not muted. Here every type of card has very different settings, so i cant tell you anything more if i cant see a screenshot of it.

PS. Skype does not detect plugged in mics or anything for that matter. It just uses the default devices provided by the PulseAudio server (be it integrated, bluetooth ot whatever).

Quick mic test: open a terminal and type 

arecord | aplay

and press enter. You can stop it with ctrl+c.

---

### Post by Lyubo on 2011-01-03
Just got back to 10.04, therefore the problem is no longer present, however 11.04 still has issues with my mic :D

Cheers

---

### Post by subinthegladiator on 2011-08-14
Hi [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640"),

Just bought a new headphone and mic, head phone works perfect. But mic doesn't works. I tried all your instructions, doesn't seems to work. I am using UBUNTU 11.04.

I saw another thread, and tried their suggestion as well, 

First what i did is installed the following packages

libao4 libasound2-plugins

Then created a new file in /etc/asound.conf and added the following values

cm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}

Then modified /etc/iibao.conf changed default value to pulse

Please let me if you can help me, Thanks in advance.

---

