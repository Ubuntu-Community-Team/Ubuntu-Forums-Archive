---
title: "set up analog headset so both aspects work at once?"
date: 2011-03-04
forum: General Help
---

### Post by poikiloid on 2011-03-04
my headset has a headphone jack and microphone jack.

if i go to sound preferences > Hardware (Tab) and select Profile: Analog Stereo Input, then I can record sound with Sound Recorder.
but in order to be able to hear what I recorded, I then have to go back to sound preferences > Hardware (Tab) and select Profile: Analog Stereo Output.

i see there is a profile option "Digital Stereo (IEC958) Output + Analog Stereo input", but when that one is selected, i can't hear anything through the speakers..., so, still having to switch back and forth as described above. perhaps a profile option with "Analog Stereo Output + Analog Stereo Input" would work, but it is not there...

why do i have to switch back and forth?  (actually, it seems this setting-switching-requirement is true of the laptop's built-in speakers and mic as well, not just the headset...)

(Everything in GNOME ALSA Mixer is unmuted and set to maximum volume. Capture is at maximum and the "Rec" box is checked...)

thanks for any help...

---

### Post by poikiloid on 2011-03-06
It seems I was finally able to figure it out:

I had to download the "PulseAudio Device Chooser", which also lead to the automatic installation of PulseAudio Volume Control, PulseAudio Preferences, PulseAudio Manager, and PulseAudio Volume Meter (Playback).

I opened the Device Chooser from the top panel (the PulseAudio applet looks like a red circle with a red slash through it). Then, from there opened Volume Control. On the Configuration tab I chose Analog Stereo Duplex. On the Recording tab, it didn't show anything until I started Sound Recorder, and started recording. While it was recording, I was able to select "Internal Audio Analog Stereo". After that, I was able to record and playback with the headset from Sound Recorder. I have not yet tried this with any VoIPs like Skype or Google Voice. I'll report again if I find any additional action is needed for those to work.

I guess with the complexity of the whole linux audio approach, with PulseAudio, ALSA, etc, you have the potential to control things with more power than as you can with the defaults on Mac/Win, but not everyone wants/needs this power. It would be nice if the defaults "just worked" for most basic use cases like they seem to do on Mac/Win...I love ubuntu & open source, but this seems like one area that can use work, as even many seeming experts have stated as well... At least, have a "Help" button on the Sound settings window, as I found it rather difficult to locate an introductory guide/primer on PulseAudio and how linux sound works in general...

---

