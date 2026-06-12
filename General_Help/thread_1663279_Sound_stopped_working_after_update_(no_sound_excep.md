---
title: "Sound stopped working after update (no sound except random pops)"
date: 2011-01-09
forum: General Help
---

### Post by ketarax on 2011-01-09
10.10 on a 6core AMD setup, was working juuuust perfect, however after the latest updates and a reboot I get no sound (in f.e. Sound Preferences -> Test Speakers, nor YouTube), except apparently random 'pops' that alternate between the left and right channels.  The pops are driving me crazier than the actual lack of sound.

I did this: [http://ubuntuforums.org/showpost.php?p=9917747&postcount=10](http://ubuntuforums.org/showpost.php?p=9917747&postcount=10)
but the problem persists. 

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

Motherboard is M4A88TD-M EVO/USB3 (without the USB3...), using analog audio.

The only way I can get *controlled* sound is by toggling Mute -- the right channel 'pops' with each toggle ... 

Any help greatly appreciated!

---

### Post by ketarax on 2011-01-10
Bumping up ... 

I've tried to get this fixed but without success.  Stuff I've tried is adding PulseAudio control software (from the software center) and toggling anything that makes sense; switching to HDMI audio (so far it's never worked, even before the present issure arose -- I can see the volume monitor bars go up and down when testing speakers, but no audio comes out of the display; yes, it has volume set to 100, and not muted).  Also tried several audio-related fixes that I've found for 10.10 (like the tsched=0 in /etc/pulse/default.pa).  Tried using the front panel speaker connector, no difference.

I'll continue trying, but meanwhile -- any ideas or even knowing if someone else has the same issue would be nice.

Back in the days I used to fix any and all sound issues simply by purging pulseaudio.  That doesn't seem to be necessary anymore, but all I need is a very slight encouragement (or a few more hours without sound) and I'll have a go at this, too :)

---

