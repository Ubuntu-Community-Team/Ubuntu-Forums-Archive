---
title: "MP3 player program problem"
date: 2009-12-13
forum: General Help
---

### Post by D4Y.V on 2009-12-13
On the program "Movie Player" that's preloaded onto Ubuntu, My MP3 files [I only use this file type] slowly decrease in volume as the song goes on and by time I'm upto 30 seconds it's completely Mute.
Infact just now I tried to watch something on Youtube, my sound did the exact same thing.
I'm using a pair of fully Working earphones.
Thanks!

---

### Post by miniyak on 2009-12-13
this seems like a plain old sound issue vs. a Mplayer issue and an odd one at that...

hmm, this is probably a longshot but, try disabling the shortcuts for sound 

(system> preferences> keyboard shortcuts)

---

### Post by miniyak on 2009-12-13
what version of ubuntu are you using btw?

---

### Post by D4Y.V on 2009-12-13
9.10, the one on the main site, Desktop.
I'm not sure how to disable them, but it doesn't look like there are any set up for it.

---

### Post by D4Y.V on 2009-12-13
Discovered how to Delete shortcuts, unfortunately that wasn't the problem.

---

### Post by D4Y.V on 2009-12-13
Hello? Still unresolved and dreading the worst here!

---

### Post by miniyak on 2009-12-13
what hardware are you using? particularly info pertaining the sound card would be useful to anyone looking at this thread

if you can you may also want to change the title to "sound changing volume level issue" or something to that effect

check system> administration > hardware drivers to see if there is any thing involving you soundcard is listed 

check system> preferences > sound to see if there are any suspiciously set setting there

I'm look at the setting on jaunty 9.04 right now... but i know the sound interface has been recently changed for karmic 9.10

---

### Post by D4Y.V on 2009-12-14
I'm not sure how to check what kind of sound card I have on this operating system.
I checked and there arn't any things stopping anything from what I can see...

---

### Post by miniyak on 2009-12-14
sorry, by hardware, I mean the physical machine

like for instance, laptop or a desktop? Integrated sound card or pci sound card? Whats the model and brand? since we are talking about sound gauging the age of the system may be a good idea

I have found in at least one case that a sound card can fail in ubuntu and work in a distro with better legacy support. In my case the distro with better legacy support was mepis

I really don't know of a way to check the model of the soundcard though ubuntu either. I guess this is because i dont need to nor will i ever. These types of things are abstracted away from the user in ubuntu for the sake of simplicity. I'm sure there is a way to bring it up through the terminal though

---

### Post by D4Y.V on 2009-12-14
Dell Dimension C521 Desktop with 9.10 Ubuntu.

---

### Post by miniyak on 2009-12-14
no red flags there, seems like a computer that should play well with ubuntu 

actually its more modern then the first computer i put ubuntu on...

maybe you have a hosed install, did you download the .iso within a week of release or write the disc at more then 16x?

Maybe reinstall ALSA 

Actually before further deliberation here you probably want to skim through this [http://https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

I was hoping there would be a simple answer I could give you, sorry

---

### Post by D4Y.V on 2009-12-14
Hi?

---

### Post by D4Y.V on 2009-12-14
Am I allowed to Bump?

---

### Post by D4Y.V on 2009-12-15
> **miniyak said:**
> no red flags there, seems like a computer that should play well with ubuntu 

actually its more modern then the first computer i put ubuntu on...

maybe you have a hosed install, did you download the .iso within a week of release or write the disc at more then 16x?

Maybe reinstall ALSA 

Actually before further deliberation here you probably want to skim through this [http://https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

I was hoping there would be a simple answer I could give you, sorry

I got it 2 nights ago, the install was perfect and the checkup before hand said the disk was absolutely fine...

---

