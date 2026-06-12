---
title: "Cannot record from speakers - only static"
date: 2010-01-14
forum: General Help
---

### Post by Saiko Berry on 2010-01-14
Okay well I am using ALSA. I'm trying to record from my speakers using default sound with gtk-recordmydesktop but I can't. All I'm getting is this;

[http://sai.lpchip.com/v/Errorsound.ogv](http://sai.lpchip.com/v/Errorsound.ogv)

No matter what I do. I HAD SOUND for like a fraction of a second one time but Ive not been able to get it back. I don't want to record from my microphone. That's easy.. I want to record directly from my speakers. Anyone know how to do this?

PS: Im also having trouble recording sound with audacity.. gives me some latency error and crashes. I have to end its process to even use openbox. Thankful for dmenu ._.

---

### Post by audiomick on 2010-01-14
> **Saiko Berry said:**
> .. I want to record directly from my speakers. Anyone know how to do this?

I think you should explain this a bit more. After all, speakers are for putting out sound, not receiving it.

Do you mean put a mic in front of a loudspeaker and record what is coming out? I don't think so, but that is what your question sounds like.

Do you mean recording the signal that appears on the speaker output connector?

Or something else?

---

### Post by Saiko Berry on 2010-01-14
I want to record game sound that is being played by a game on my computer. For example, recording the sound on an emulator or whatever to a desktop record program. All Im getting is static. The video I attached in my post is me recording sound while that game is being played, but focusing the window on the alsa mixer instead. Ive tried all kinds of combinations but I can not get sound to record through my default device.

---

### Post by audiomick on 2010-01-14
Ok.
I am afraid I am going to run out of ideas very quickly. I don't really do audio stuff on the computer.

I think I would attempt an "old fashioned" solution, i.e. connect line out (speaker out) to line in with a cable.

To do it internally, the question is if the ALSA mixer anticipates wanting to do something like that? Maybe not, it is a bit out of the ordinary.

---

### Post by Saiko Berry on 2010-01-14
...what?

---

### Post by audiomick on 2010-01-14
> **Saiko Berry said:**
> ...what?

what do you want clarified?

---

### Post by Saiko Berry on 2010-01-14
All I have are a pair of speakers, and a green audio plug that plugs into one of my colored audio jacks.

---

### Post by audiomick on 2010-01-14
Is it a laptop or a desktop?

---

### Post by Saiko Berry on 2010-01-14
Desktop.

---

### Post by sxmaxchine on 2010-01-14
this sounds like a problem i had i fixed it by opening the sound preferences and in the recording tab i mutted the volume thing labeled capture (sounds strange) then in the switches tab i checked both headphone jack sensor and mix mono and left all the others unchecked.
also if u dont see these controls you may need to add them by clicking the preferences button.

hope this helps

---

### Post by Saiko Berry on 2010-01-14
I don't have any of those.. I attached a video that shows my mixer gui.

---

### Post by audiomick on 2010-01-14
Ok. First of all, just so you know where I am coming from. As I said, I don't really do much audio stuff on the computer. On the other hand, I work as a sound technician, and have done for about 25 years.

As far as the cable connection on the outside goes: You take the signal for your speakers from the green socket on the back of the computer, more than likely. Or on the front, maybe, anyway it is almost certainly green.

You mentioned recording from a mic: that gets plugged into a socket that is generally red. 

What I mean is connecting these two sockets with a cable. It is electronically not exactly correct, but it should work.

What you have to be aware of is that the loudspeaker output is stereo, a 3 pin connector, and the mic input is mono, a 2 pin connector. The appropriate cable should be easy to get from a hi-fi shop. They are usually called something like "stereo to 2 x mono y cord"

As far as the internal way goes, the question is whether the alsa mixer is capable of directing the stream of audio that the game is producing back into the recorder. I am afraid I don't know, and I can't look because I don't have the alsa mixer installed. It is possible that the mixer can't do this, as the mixer may only be built to send out or take in, but not do a "u-turn".

The process to follow would be identify the audio stream from the game, that is the one which turns the game sound off when you mute it (not the master, of course) and then look for a way to assign that stream to the input of the recorder.

---

### Post by Saiko Berry on 2010-01-14
I know it can because I had it working for the foobilliard game a bit ago but I only had it working for a few seconds, changed something and it broke again. I havnt been able to get it back.

The only response I got was from the "Digital" bar when I raised it, but now I dont get anything from that either.
Thing is, in gnome sound recorder It forces me to record from "Digital".

---

### Post by audiomick on 2010-01-14
I've just installed the alsa mixer to have a look at it.
About all I can suggest is to go to the sound card preferences under edit and make sure all options are checked to make sure you can really see all possibilites.

---

### Post by Saiko Berry on 2010-01-14
Done and done. Ive also checked out the xfce mixer which is a lot nicer and better put together. Problem still is I can't get audio from my sound card. I can hear it just fine, but it isn't recording.

My capture things are; Capture, Capture 1, Digital.

I tried every possibly combination of the three, and Ive not been able to get it working. I don't know why considering I had it working briefly for the pool game this really doesn't make much sense. If I CAN HEAR IT why can't my computer. Sigh.

---

### Post by Saiko Berry on 2010-01-14
[http://sai.lpchip.com/f/Alsa_Info.txt](http://sai.lpchip.com/f/Alsa_Info.txt)

---

### Post by Saiko Berry on 2010-01-15
Update: I tried with like every audio recording program out there, I even tried to pull the sound from my speakers around with Jackd but nothing. The only possible way it seems that I can record the sound from my computer is to stream it through my microphone but that produces really shitty quality.

Anyone have an alternative?

---

### Post by Saiko Berry on 2010-01-20
Bump. Im using an NVIDIA sound card.

---

