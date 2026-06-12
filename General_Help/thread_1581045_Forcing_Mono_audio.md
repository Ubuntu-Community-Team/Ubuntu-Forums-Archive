---
title: "Forcing Mono audio"
date: 2010-09-24
forum: General Help
---

### Post by Woody_Paranoia on 2010-09-24
Okay, long story short. My speakers are broke, I can't afford new ones as yet. So I've got my computer audio plugged into my amp. However, it's only coming out of one channel (right, I think). So I need to set my sound output as mono so I can hear my music properly :sad:

I have searched and searched through loads of different forums etc. but can't find any solutions. There is a reoccurring theme coming up telling me that either ALSA and/or PulseAudio should be able to do this for me. However after installing both I'm still getting nowhere with my problem.

I'm starting to think that maybe it's my sound device being unable to do mono? But yet, logically I don't see why it wouldn't.

Any extra information you need, just ask and I can gather it for you :)

---

### Post by Woody_Paranoia on 2010-09-25
Bump =|

---

### Post by mrhhug on 2010-09-25
hmmmm i would just launch gnome-volume-control go to output tab and then change the balance all the way to the working speaker.. 

is that an option

---

### Post by Woody_Paranoia on 2010-09-26
I feel so stupid it's unreal.

I tried this, and it just made the sound go all crackly and distorted... Turns out if I move it one tiny little bit away from the very end of the bar it sounds fine.

Urgh, solved, even if I was stupid about it :)

---

### Post by Woody_Paranoia on 2010-09-26
Oh no, this hasn't solved my problem.

Listening to music and sometimes I only hear the one part still...

Any other suggestions anyone? :confused:

---

### Post by Woody_Paranoia on 2010-09-30
Bump](*,)

---

### Post by mrhhug on 2010-09-30
ok how about trying this? it seems like a boatload of work but.....
install jack
```
sudo aptitude install jackd qjackctl
```
there is a walkthrough of perfect installation here: [http://ubuntuforums.org/showthread.php?p=5038203](http://ubuntuforums.org/showthread.php?p=5038203)

launch jack with the command ```
qjackctl
```
click on settings: change the output channels to 1 (see attached)

that should do it!

---

### Post by Woody_Paranoia on 2010-10-01
After a bit of fiddling I have managed to get it to run so it doesn't stop after 2 seconds...

But there is no sound coming from my rhythmbox. I've looked into solutions but nothing seems to work with me.

To be honest, I might just give up and stick with one sided audio, this seems to much effort for something that I thought might have been quite simple. 

Thanks for your help anyway =]

---

