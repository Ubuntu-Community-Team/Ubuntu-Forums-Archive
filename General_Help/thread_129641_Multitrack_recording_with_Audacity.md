---
title: "Multitrack recording with Audacity"
date: 2006-02-14
forum: General Help
---

### Post by zombie on 2006-02-14
I'm trying to record a bassline to a song through audacity but I need the original track playing whilst I record the bass. The problem I'm getting is that when I press record not only am I getting the bass in the new track i'm also getting the original track. This means I can't set the volumes correctly as i'm only getting a quiet signal from the bass. I've tried running killall esd before starting audacity to no effect, also it seems to record any sound being played e.g. an mp3 being played by xmms gets recorded. My sound card is a soundblaster audigy using the emu10k1 driver according to my volume properties. Anybody come across this problem before and if so can you point me to the fix

---

### Post by gosh on 2006-02-14
Can't you import the backing track to one track in audacity and your bass on another.
Then when you record make sure monitoring is on and you should here both tracks and record just one.

---

### Post by zombie on 2006-02-14
The backing track is imported into audacity then I hit record and play along but the new track still records the original plus my bass. I have tried creating a new track from the menu but can't seem to do anything with it once it's there.

How do I check monitoring? the only option I have seen in audacity is to play current tracks whilst recording.

---

### Post by gosh on 2006-02-14
[QUOTE=zombie]How do I check monitoring? the only option I have seen in audacity is to play current tracks whilst recording.[/QUOTE]

monitoring = play current tracks whilst recording :) 

Do you have two seperate tracks? One for the backing track and one for the bass. And did you select one for recording and the other for only playback?
I don't have audacity in front of me now, but I'll look into it when I'm home.

In the mean time, you might also take a look in : [http://audacityteam.org/forum/](http://audacityteam.org/forum/)

---

### Post by aeiah on 2006-02-14
if you've set the options correctly for it to play the original track at the same time as recording the new one (which it seems like you have), and it still records input and pre-existing tracks together then it may be the limitation of your soundcard.

ive been using audacity for a while now, on windows (ive only just installed linux). whilst i can record fine with my audigy, and can multi-track now i have my m-audio delta 44, a bandmate uses his girlfriend's laptop, and the soundcard limitations mean that he has the exact same problem as you. perhaps it is a soundcard driver problem or driver limitation under linux. do you have your machine dual booting with windows? if so, install audacity in windows and see if you get the same problem with the same settings

---

### Post by zombie on 2006-02-14
Looks like it's time for a new card for me then:( 
The m-audio range looks nice.

---

### Post by aeiah on 2006-02-14
try some tests before jumping to a massive conclusion though! those audigy cards are really nice for playback and low cost single-input audio if you can get it working properly, if its possible. 

ive had to leave my audigy out of my new pc because its small form factor and the 1st pci card just about sits on my gfx card fan :( so i havent the opportunity to test it easily. if your motherboard has onboard sound, it may be possible for you to route the sound output through there, and use your audigy just for audio-input (or vice versa), this may side-step the problem but ive never tried it.

but yea, those m-audio cards are great. well, i can only speak for the delta-44, but its a fantastic little thing for £100. the break-out box is tough as hell and the sound is crystal clear. dont know what the linux support is like, but ubuntu's auto-detection for it isnt perfect. it outputs sound but its all in slow-motion and at the wrong frequency. ive yet to have a look at the problem...

---

### Post by aeiah on 2006-02-14
this may be of some relevance: [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

---

### Post by zombie on 2006-02-15
I think i've finally got this working :D I need to turn the pcm capture off in alsamixer before running audacity and it starts working as it should. unfortunalty i've now messed about with all the other settings in the mixer and seem to have knocked the sync out for tvtime. Anyone know how to reset my alsamixer back to it's default settings for my card?

---

### Post by teledyn on 2008-04-18
:guitar:This is a side-related topic because someone brought up the m-things but said the Linux support was not good so that leads me to ask: *What _is_ a good solid musician's sound-system solution for Ubuntu?*  Ideally I'd like it to be small and portable to move with my (Dell Inspiron) laptop and I'd like to use Audacity to record tracks, and extra bonus points if it has a patch-uploadable MIDI system!

I recently saw an Edirol UA-1EX USB Audio Interface for sale on eBay for $75, would something like that do the trick?

---

