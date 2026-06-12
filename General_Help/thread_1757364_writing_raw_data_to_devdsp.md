---
title: "writing raw data to /dev/dsp"
date: 2011-05-13
forum: General Help
---

### Post by LanguidLegend on 2011-05-13
I'm having trouble with a little exercise in my CS class:
[INDENT][COLOR="DimGray"]_Redirecting mouse device into a file_
sudo cat /dev/input/mice > rawmouse.data
*Note that on some distro's you'll need to sudo to bypass device files' restricted permissions.*

Move the mouse a bit and then type CONTROL-C.

Now, cat that file to the sound card.

cat rawmouse.data > /dev/dsp

Sounds horrible, doesn't it?
So that's how we make sound, by throwing bytes at the sound card.[/COLOR][/INDENT]
Here's my issue: I follow those directions, but it remains silent.. Any ideas why?

_Note:_ I am running Ubuntu 10.10, and my sound is at max volume.

---

### Post by Trinexx on 2011-05-13
/dev/dsp is an OSS (Open Sound System) device. Ubuntu no longer uses OSS, so /dev/dsp doesn't exist.

---

### Post by LanguidLegend on 2011-05-13
Ah, I see. Well he did mention some alternatives to /dev/dsp:
[INDENT][COLOR="DimGray"]These are the most standard device file names, some Linux distributions may use slightly different names.

/dev/audio
normally a link to /dev/audio0

/dev/audio0
Sun workstation compatible audio device 

/dev/audio1
second audio device

/dev/dsp0
first digital sampling device

/dev/mixer0

/dev/music

/dev/sequencer

The PC speaker driver provides the following devices:
/dev/pcaudio

/dev/pcsp

/dev/pcmixer[/COLOR]
[/INDENT]
However, I don't see any of those.. What does Ubuntu use?

---

### Post by LanguidLegend on 2011-05-15
How can I find/access Ubuntu's ALSA sound system if not /dev/dsp?

**Update:**
Well I've done some more digging, and I've come across a directory which might contain my solution(?): /proc/asound

Any ideas? Am I heading in the right direction??

---

