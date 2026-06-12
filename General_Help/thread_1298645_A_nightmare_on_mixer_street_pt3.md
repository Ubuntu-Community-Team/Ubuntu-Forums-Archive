---
title: "A nightmare on mixer street pt3"
date: 2009-10-23
forum: General Help
---

### Post by nerdistmonk on 2009-10-23
So I got my soundcard that has bass and decide to go to Ubuntu 9.10 and what do I see, it sure isnt a mixer with sliders to let me control said bass? Really? Seriously? I understand gnome being simple, but give me a friggin break, even windows had a slider for bass, So my first instinct was to grab a large hammer, lurk behind pulseaudio and yell DIE DIE DIE DIE JUST DIE! (Purge) BUT what do you know?

Not only do I no longer have a mixer but I just killed the only sound applet in gnome panel? and to top off this turd-sundae, every time I boot it resets to 100% max audio, I have loved ubuntu for a very long time, but why???? Why would you give me just ONE slider for volume? I mean what next....will my screen resolution be permanatly locked at 1440x900 so I cant use my older monitors? (Im sorry if I come off angry, but I went through 2 threads and alot of annoyance to get good sound, just to have it pulled out from underneath me)

I guess im going to use debian, at least they dont make crazy changes like this.
(Flame me or bash me for this, it was still a piss poor design decision, how am i supposed to mute the other 29 sliders on my card that put off EMF noise? I checked this applet up and down, so now I got a crippled alsa, a not as good mixer and no applet and MAX VOLUME!!!! every time I log in)

Before I was upset because me 2 soundcards didnt work, I manned up and spent the money on 2 new soundcards, but this ones out of my hands. 

EDIT: Add to the list that the 9.10 RC is throwing me kernel problem errors like a swarm of angry bees. erm

--Once again I apologize for my aggravated tone, but really?

---

### Post by P4man on 2009-10-23
if you're referring to the equalizer in amarok, then [you have to wait for Phonon to be released for karmic.]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/448245") Its not there yet, Karmic is still in beta, what a shock.

As for muting all channels by hand, there is still alsamixer. I also happen to like the new pulseaudio features, and the interface is a whole lot more logical than the various sound and volume windows in jaunty.

The 100% volume on startup might be a bug. At least its not like that on my setup. Rather than ranting here, you might want to check launchpad for a bug and file one if none exists. After all, thats why you downloaded a beta, to test it and help improve it by reporting any bugs, right?

---

### Post by nerdistmonk on 2009-10-23
> **P4man said:**
> if you're referring to the equalizer in amarok, then [you have to wait for Phonon to be released for karmic.]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/448245") Its not there yet, Karmic is still in beta, what a shock.

As for muting all channels by hand, there is still alsamixer. I also happen to like the new pulseaudio features, and the interface is a whole lot more logical than the various sound and volume windows in jaunty.

The 100% volume on startup might be a bug. At least its not like that on my setup. Rather than ranting here, you might want to check launchpad for a bug and file one if none exists. After all, thats why you downloaded a beta, to test it and help improve it by reporting any bugs, right?


UM dude im talking about the gnome mixer applet that used to work just fine and then it was butchered and stripped down to just a SINGLE slider, I hate kde, I refuse to use it or amarok


EDIT: I see this is going to be a repeat where no one actually reads the whole thing so I spend 40 posts trying to describe the "problem" that was created that DIDNT exist in 9.04 because 9.04 had a FULL mixer in gnome. Im already downloading the debian sid cdrom.

And yes theres alsa mixer, but then pulse gives more headaches

---

### Post by P4man on 2009-10-23
gnome mixer on karmic. Whats missing?
[IMG]http://img17.imageshack.us/img17/3332/screenshot004w.png[/IMG]

---

### Post by nerdistmonk on 2009-10-23
Well whats the package name? that picture isnt helpful, you put that monster pic on there like its a trophy, I was talking about the volume mixer up by the clock, I have a sound icon by the clock but no mixer, so lets try this again.

---

### Post by P4man on 2009-10-23
I was too lazy save/resize/save/upload it (its a one click auto upload from a screenshot using shutter)

Anyway its  gnome alsa mixer, which you can install from the software center like anything else. And before you say its alsa and not pulse, realize pulse is just a framework on top of alsa. The channel mixing and equalizer are done through alsa anyway.

You can create a launcher for it if for some reason you need it often or you can probably put it in the tray using alltray

---

### Post by DeMus on 2009-10-23
> **nerdistmonk said:**
> Well whats the package name? that picture isnt helpful, you put that monster pic on there like its a trophy, I was talking about the volume mixer up by the clock, I have a sound icon by the clock but no mixer, so lets try this again.

Maybe you don't notice it but people here are trying to help you, even though they don't have to. Your sarcastic comments don't help at all.
I was taught: you catch more flies with honey than with vinegar.

---

### Post by nerdistmonk on 2009-10-23
> **DeMus said:**
> Maybe you don't notice it but people here are trying to help you, even though they don't have to. Your sarcastic comments don't help at all.
I was taught: you catch more flies with honey than with vinegar.

... I guess you didnt read my original 50 post thread, where I spent more time explaining and being bashed than actually getting help, debian is bumkiss I cant get it to load, I am trying out crunchbang linux (no pulseaudio to be found), but thanks anyways, even with the mixer my applet is gone forevermore and I dont like this trend of dramatic changes to the OS and then be lectured on it.

--my final post, signing off

---

### Post by P4man on 2009-10-23
You call that dramatic change? Well.. ok.
If you dont like such change, there is always the option of not upgrading.

As for being lectured; I havent seen the other posts, nor do I think I posted in it, in this thread you're the one ranting and lecturing the community thats doing all the hard work, just because you no longer see the bass slider and dont know how to get to it. Sounds rather ungrateful to me considering how much money and effort you likely poured in this project.

But hey, its a free world and free software. So if you find a distro that puts the equalizer *exactly* where you want it, then have fun with it.

---

### Post by nerdistmonk on 2009-10-23
> **P4man said:**
> You call that dramatic change? Well.. ok.
If you dont like such change, there is always the option of not upgrading.

As for being lectured; I havent seen the other posts, nor do I think I posted in it, in this thread you're the one ranting and lecturing the community thats doing all the hard work, just because you no longer see the bass slider and dont know how to get to it. Sounds rather ungrateful to me considering how much money and effort you likely poured in this project.

But hey, its a free world and free software. So if you find a distro that puts the equalizer *exactly* where you want it, then have fun with it.


I wasnt going to post again but since you went beyond what I consider forum conduct and delve into the mystery of how much money I spend on linux heres a break down:

Been using ubuntu since version 6
For me to use 6 I had to build a different computer, it didnt like my new one, that ousted me $200 (bought through the debian site), Thats just for starters, I have donated $85 of my money to various linux projects and today I spent $15 total on 2 new soundcards because of my "lecturing" about the bass slider..... SO please dont tell me I dont do my part, this will mark the first time I leave ubuntu. 

Thats a light overview, im not going through my bank records to give you a breakdown and yeah as for not upgrading, I already have a solution, im switching to something else

---HAVE A NICE DAY SIR, Signing off.

---

### Post by VertexPusher on 2009-10-23
Note that the Gnome ALSA mixer is adaptive, i.e. it will only expose controls supported by the underlying driver. So if you don't see bass and treble sliders, they are either hidden from view (See the mixer preferences!) or don't exist at all.

In fact, very few sound cards have a built-in EQ, because line-out connectors are supposed to carry an undistorted signal with linear frequency response. Bass and treble are supposed to be controlled by the amplifier that the sound card is connected to.

---

### Post by P4man on 2009-10-23
I just wasted some time reading your posts. All I can see is people trying to help (or in some cases explain) while you seem deaf to advice and rant and bark up the wrong tree. For instance, you insist its linux fault that your x-fi is not properly supported, while failing to realize who is really to blame for the debacle:
[http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1](http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1)

despite ppl trying to explain to you. Then you take this sarcastic (if not downright rude) attitude towards the community., 

As for how much you paid for your soundcards or donated; I just dont care. No one forced you. You might have donated more than Mark Shuttleworth and you'd still be wrong, and Id still not appreciate the attitude. Needless to say, if you intend to move to another OS or not, is hardly my concern. At least I hope the advice given here and elsewhere will serve someone else.

/me signing off.

---

