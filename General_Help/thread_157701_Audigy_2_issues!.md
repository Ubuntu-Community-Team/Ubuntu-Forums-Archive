---
title: "Audigy 2 issues!"
date: 2006-04-09
forum: General Help
---

### Post by Face1 on 2006-04-09
Okay, so I installed ubuntu yesterday for the first time, and I'm pretty happy with it, seems to work great so far.  ...except for sound.  I have an Audigy 2 soundcard, and I cannot figure out how to get the sound working properly.  At this point, sound is only playing out of the "Line out 1" port ([Look at the picture about a quarter of the way down the page to see what I'm talking about]("http://www.3dvelocity.com/reviews/audigy2/cla2_2.htm")).  Now, it's nice that I have some sound playing, and it sounds good, but my 5.1 system is unhappy.  
I'm using alsa...I think (I'm a bit of a newbie at this--for all I know the problem could be that I'm not really using alsa).  And that's pretty much all I have to go on.

Any suggestions?

---

### Post by BoyOfDestiny on 2006-04-09
[QUOTE=Face1]Okay, so I installed ubuntu yesterday for the first time, and I'm pretty happy with it, seems to work great so far.  ...except for sound.  I have an Audigy 2 soundcard, and I cannot figure out how to get the sound working properly.  At this point, sound is only playing out of the "Line out 1" port ([Look at the picture about a quarter of the way down the page to see what I'm talking about]("http://www.3dvelocity.com/reviews/audigy2/cla2_2.htm")).  Now, it's nice that I have some sound playing, and it sounds good, but my 5.1 system is unhappy.  
I'm using alsa...I think (I'm a bit of a newbie at this--for all I know the problem could be that I'm not really using alsa).  And that's pretty much all I have to go on.

Any suggestions?[/QUOTE]

Mine is a Audigy2 ZS. Use ALSA. ESD is well, I'd break forum rules if I explained how I feel about it....

With ALSA multiple sound from multiple apps, 5.1, etc works perfectly.
make sure to download alsa-oss too. 

try
sudo killall esd
if that fixes things (which means ESD was ruining things...)
disable sound server in Sound (in system -> preferences and make sure the audigy is the default card)

Multimedia selector -> make alsa the default output

Also, check the volumes for the speakers, in the mixer you can add channels for center and sides, etc. I had to turn mine up to get sound for the rear speakers...

---

### Post by Face1 on 2006-04-09
BoyOfDestiny, okay, I did that, but nothing changed...I don't think I was using it anyway.  And yeah, I have alsa-oss already.

---

### Post by Face1 on 2006-04-10
anyone?

---

### Post by BoyOfDestiny on 2006-04-10
[QUOTE=Face1]anyone?[/QUOTE]
I hate to suggest this (kind of a last resort thing)... Have you considered trying one of the dapper flights? I've been running dapper on my desktop 24/7 since January... It's a point where I feel comfortable recommending over breezy...

Even if you don't want to install it, a livecd would let you know that the hardware works, and it's some bug that already been ironed out...

[http://cdimage.ubuntu.com/releases/dapper/flight-6/](http://cdimage.ubuntu.com/releases/dapper/flight-6/)

Good luck, I hope you get sound working soon!

---

### Post by Face1 on 2006-04-10
Okay, thanks, I'll burn a liveCD and try that, but I'd rather not go through a whole reinstall again at this point if it is at all possible.

If any of you aren't aware of how to solve my problem, would you be willing to maybe point me in the direction of somewhere else I could ask?  Thanks.

---

### Post by Face1 on 2006-04-10
Okay, **[SIZE="3"]update[/SIZE]**! --Time to change my question a little.  Something has changed (which I guess is my fault, but I don't know exactly what I did), and now I'm not getting any sound at all!  So I'm not sure what the problem is.  I've played with alsamixer a little, but to my knowledge I didn't do anything specifically to causes this. 

Also, (and I should have mentioned this originally) I have integrated sound on my motherboard (some Intel sound chipset).  So, any changes I make I have to be sure to be for the audigy, not the Intel stuff.

Any ideas?  Maybe there is a site somewhere that I haven't been able to find, that has an outline of what my sound settings should be like?

Thanks again!

Oh also, I'll add that I'm willing to recompile the kernel, if maybe that will help (modules, I suppose).  I've done it before with some success, but [this]("http://ubuntuforums.org/showthread.php?t=157560") make it a sinch!

---

### Post by Denis on 2006-04-11
I also have an Audigy 2 ZS. The sound works here, except for games. I also have an internal soundcard too. If you don't have any soud at all, you could check the following: 

Open "alsamixer -c 1" in the terminal (this will open the mixer of your 2nd soundcard). Take a look at the different sliders and mute buttons (press m to mute/unmute). Turning some things on may allready help you. You should definitely make sure that Audigy Analog/Digital Output Jack is not muted, since otherwise you would have no sound at all. 

I hope you can fix the sound quickly. I don't think recompiling the kernel will help, that would be a waste of time.

---

### Post by bionnaki on 2006-04-11
yup, I have the same card. you have to unmute Audigy Analog/Digital Output Jack. thats how you get sound.

---

### Post by bobpur on 2006-04-11
I had a similar problem once. I had to go into BIOS and disable onboard sound and then go delete the drivers for the onboard sound.As a matter of fact, I deleted all sound drivers and installed the ones I needed (Soundblaster 5.1 X-gamer).

---

