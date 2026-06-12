---
title: "Virtual Keyboard Jack, Qsynth, qjackctl No sound"
date: 2011-01-21
forum: General Help
---

### Post by hwttdz on 2011-01-21
I'd love to get a physical musical keyboard and connect it to my cpu, but before doing this I'm trying to get all the software set up to make sure it's possible.  I've followed a few different tutorials, and it seems that between zynaddsubfx and qsynth (or at least from what I've read), I can get more realistic sounds from the latter so that's what I'm working on at the moment.  I followed this tutorial [http://ubuntuforums.org/showthread.php?t=1003466](http://ubuntuforums.org/showthread.php?t=1003466) (and needed to do this [http://ubuntuforums.org/showthread.php?t=276499](http://ubuntuforums.org/showthread.php?t=276499) to get a snd-seq issue ironed).  

So where I stand now is that I can start qsynth, vkeyboard, and qjackctl.  I can successfully link the virtual keyboard with the synth input in qjackctl.  A soundfont (fluid-soundfont-gm) is loaded. And when I click on keys on the virtual keyboard the little light in qsynth lights up (I suppose implying that it's doing something).  Of course now we get to the issue which is that despite things appearing that they're working well, there is no sound.  And yes speakers are on, volume is up and sound works in every other way (I'm listening to music as I write).  

So any suggestions?  I don't see much in the way of error messages, 

qsynth complains that:
fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
Cannot lock down memory area (Cannot allocate memory)

This is despite me giving the audio group realtime privileges during the jack install (but I didn't add me to audio), didn't read any mention of this anywhere.

---

### Post by hwttdz on 2011-01-24
Bump.

---

### Post by hwttdz on 2011-01-27
Bump.

---

### Post by dewdrop_world on 2011-01-27
Maybe ask in the Ubuntu Studio forum? This is more specific than "General Help."

I've a couple of other comments, but no time right this second. Later... (soon...)

---

### Post by dewdrop_world on 2011-01-27
What I mean is, even if you aren't using "Ubuntu Studio" proper, chances are most of the people reading "General Help" have no idea what qjackctl/jackd is. Whereas, under Ubuntu Studio, many more people will be familiar with these technologies.


I didn't read closely, but I remember hearing of a number of audio related bugs in 10.10. At least, it was enough to make me not want to upgrade.


> "but I didn't add me to audio"


You probably need to do that. If you're not in the audio group, processes that you launch will not have real-time privileges, no matter what else you do.


> "I'm listening to music as I write"


Are you using a jack-capable application for listening, or the more usual pulseaudio-based apps? I had to take some fairly extreme measures to get pulse to play nice with Jack (i.e., install jack2, use the falktx "pulse-jack" script, and install a real-time kernel).


I think amarok2 comes with Jack support.


What does meterbridge tell you about what's going into/coming out of jack? You should be able to monitor qsynth's output directly.


James

---

### Post by hwttdz on 2011-01-27
Cross posted at [http://ubuntuforums.org/showthread.php?p=10404465#post10404465](http://ubuntuforums.org/showthread.php?p=10404465#post10404465)

---

### Post by hwttdz on 2011-01-27
Preliminarily it appears like there is an issue with qsynth, fluidsynth (which lacks a similarily sexy gui) gets me sound!  Of course I installed and removed more packages than makes me feel comfortable. So I'll probably figure out a more direct route when I next reinstall.

---

### Post by hwttdz on 2011-01-27
And re: adding the user to audio.  This is just to get realtime priority for memory and whatnot.  But I feel more comfortable not having this, as really I don't know what I'm doing and I'd happily take away my own root priviliges if there was someone I could tell "I want a virtual keyboard that sounds like a real piano, make it so".  Latency shouldn't be much of an issue on pretty high performance hardware.

And also, here's a fedora thread that addresses some issues that some might have with getting this set up.  
[http://forums.fedoraforum.org/showthread.php?t=192384](http://forums.fedoraforum.org/showthread.php?t=192384)

---

