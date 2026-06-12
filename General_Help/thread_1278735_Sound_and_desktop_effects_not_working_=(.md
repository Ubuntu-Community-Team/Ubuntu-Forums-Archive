---
title: "Sound and desktop effects not working =("
date: 2009-09-29
forum: General Help
---

### Post by Fc1032 on 2009-09-29
Hello everyone!

dad recently picked up an old comp. Not surprisingly, it had windows and a password protected account. My windows XP and Vista discs are all recovery and only work with the default machine. So my only option was installing ubuntu, if i wanted the machine to work.

So i installed it. Problem is there is no sound at all and not desktop effects.

I've tried:
*updating using update manager

*installing ubuntu restricted extras 

*Installing desktop effects in add/remove. then i tried to turn on the effects, it said installing drivers then "could not be enable... etc"

*I've tried messing around the system>preference>sound. Changed it to all possible options, none of which worked.

*I've ran "alsamixer" in the terminal and unmuted everything.

*I follwed an online guide, removed pulseaudio and installed alsa only. Still nothing. Probably wasnt such a good idea...

*I think i might need to add something to "/etc/modprobe.d/options" but don't know what.

At the moment, i don't know what to do. alsamixer in the terminal doesnt work now (probably cause i removed something =S). I'm not that worried about the desktop effects, but i definitely need to get the sound working.

My sound driver is: "realtec ALC655". I can't find any other form of information like display drive or motherboard...
 

Any help would be appreciated =) THANKS!

---

### Post by Chriswilkie on 2009-09-29
im sorry to say some computers are to old to run effects but even if they could I would not because effects could really reduce the speed of your computer and they wouldnt even look good because frame by frame movment

---

### Post by lrcaballero on 2009-09-29
Perhaps, when it had windows installed, it was missimg the drivers for the sound card???

also try using a windows live cd to install drivers for sound and graphic card, that only ofcourse if you are dual booting.

Another option is go into your Bios and see if sound is disable (if applicable)

---

### Post by Fc1032 on 2009-09-29
@Chriswilkie: Yea, guess your right. Sound is my first priority at the moment. Pentium 4HT is OLD XD =) good thing is this comp is custom built and allows overclocking (at the moment i overclocked by 5%)

@lrcaballero: I think it had sound when it ran windows, cause it would give me that annoying sound when i typed the wrong password. I also tried the BIOS settings, the audio is on =(

---

### Post by Chriswilkie on 2009-09-29
then check your sounds prefrences in ubuntu because as far as I know if it works on windows [the worst operating system] then it should work 5 times better on ubuntu

---

### Post by Fc1032 on 2009-09-29
Hey Chriswilkie,

I've tried the preferences before and non of them work.

I have this rather "crazy" idea. You know how you said if it work in windows, it will work in ubuntu? Can i perhaps install win7 (i have the RC floating around, just remembered), and get the drivers to work there, then install ubuntu again (dual boot)?

---

### Post by tnt533 on 2009-09-29
I've had an issue here and there with hardware not being detected properly on install with Ubuntu. A reinstall fixed the issue with my sound. There are some older cards of all hardware types that may just be too old for the current modules and may need some extra nudging to work. I would try googling the make/model of your card and Ubuntu and dig through the posts you find. 

As for the video, what video card is in the box? Nvidia? ATI? What model?

---

### Post by Fc1032 on 2009-09-29
@tnt533

I was wondering if it was too old too. Thing is 9.04 runs fine on a similar pc we have (well its pentium 4 as well, has same ram...) Turns out that this comp doesnt read DVDs!!! OMG... But that might be because its HP and is overall more supported than custom built pcs?

Not sure what video card it is... cause i don't know how to check =P

I'll try running some older ubuntus (maybe other derivatives i have lying around too)

---

### Post by Fc1032 on 2009-09-30
OMG this is sooo embarassing...:oops::oops::oops:

Turns out i forgot to plug in the speaker cable 8-[

Sorry everyone :oops:

^^ well since the sound problem is solved, i guess thats it. desktop effects? forget it :p i think its fine the way it is now anyway 

Thanks for everyones help!!

---

