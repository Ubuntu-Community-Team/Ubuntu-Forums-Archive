---
title: "My Speakers Are Driving Me Insane"
date: 2010-10-10
forum: General Help
---

### Post by SnedSneeden on 2010-10-10
So i have this pretty nice logitech speaker system with an amp and everything and its worked spectacularly until about 2 days ago. Out of nowhere it starts to make this weird noise when its on. I know putting other electronics near the speakers can cause strange noises, like when my laptop is near them, but I have not moved the speakers or my computer or placed anything near it which is why its driving me insane. When I unplug it from my computer and hook it up to my ipod or droid it plays perfectly with no weird noise which leads me to believe it has something to do with my computer, although i have no idea what. Ive also noticed that some other things have been acting strange with ubuntu lately, like my resolution. I often switch between my two monitors and normally i use the same resolution for both, but now out of the blue, one of the monitors cant display that resolution and it goes a little off the screen on the other. Any help on this would be awesome, especially the speakers.. Thanks..

---

### Post by harrismh777 on 2010-10-10
Well, one problem at a time. One thing that you might try is to open your volume control (the full control with all the sliders) and make sure that unused inputs are either turned down or muted. For instance, sometimes the front-mic input will cause a fierce white-noise if the input is turned up and the mic is not plugged in. 
Just turn down (or mute) everything except Master, PCM, and Front.

You might also have some problem in your audio card. If your system has on-board video and audio the two problems may be related... static damage (lightning, etc). 

The problem is not in the sound system (external) if it works ok with your iPod.

Your system might have an open ground loop ...  but doubt it.

:confused:

---

### Post by SnedSneeden on 2010-10-10
Messing with the inputs dident really do anything, and they were already muted.. I do have on board audio and video though. Is there any way to see if that is the problem?

Edit: Now that ive messed with it more, i think it does make that sound on my ipod just very, very quietly whereas its pretty loud when connected to my computer. Also i forgot to say that the noise gets louder as you turn the volume down on the external knob, being loudest all the way down and almost in audible when all the way up. I guess it probably is my speakers then? Could they be blown or something?

---

### Post by andrewthomas on 2010-10-10
Did you read the sticky on the top of the page?
 
[http://ubuntuforums.org/showpost.php?p=9948061&postcount=2](http://ubuntuforums.org/showpost.php?p=9948061&postcount=2)

---

### Post by SnedSneeden on 2010-10-10
I tried that and it dident work..

---

### Post by harrismh777 on 2010-10-11
> **SnedSneeden said:**
> Now that ive messed with it more, i think it does make that sound on my ipod just very, very quietly whereas its pretty loud when connected to my computer. Also i forgot to say that the noise gets louder as you turn the volume down on the external knob, being loudest all the way down and almost in audible when all the way up. I guess it probably is my speakers then? Could they be blown or something?

Yes. Some external powered speakers have this problem right out of the box. The amplification (usually op amp, power op amp) is achieved through feedback, and if this isn't done properly (say pricey) then what you get is low level white-noise and|or feedback oscillation. 

Again, if you have the same symptom connected to the iPod, then its in the external speaker system.

---

