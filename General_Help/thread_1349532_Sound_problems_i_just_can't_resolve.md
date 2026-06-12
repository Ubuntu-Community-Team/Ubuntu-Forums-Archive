---
title: "Sound problems i just can't resolve"
date: 2009-12-08
forum: General Help
---

### Post by Groundswell on 2009-12-08
uh oh, here i am, posting on the forums, must mean i gave up on something ](*,)
i've been searching for weeks and have even toyed with other distributions trying to find a solution to my problems, but i just can't seem to find one.

The general idea is... I would like to run Teamspeak(linux version) and il-2 1946(windows game on wine) and recieve sound from both applications.

Yes i've accomplished this, but the sound tends to be... not so pleasant. If i use ALSA for the wine app, and let teamspeak run in pulse audio (just by launching with padsp) sound in the game is a bit laggy, bu nothing to cry about, however in teamspeak the mic input is terrible to the point where no one and understand me.

|> -If i however, run the game in OS, the sound is pretty damn good, but then i can not |have sound streams coming from any other apps.
|> -if i however, remove the padsp option from the teamspeak launcher, sound id very |good and very clear, but then i can not have sound from any other apps.
|
 \<-so i'de like to get these two guys working together and playin nice, at least the outcomes, while allowing sound from other apps
I've tried very very hard to understand the mess of "sound support":lolflag: in ubuntu but there's so many damned layers to the mess that i really just can't even guess at where the problem is. I've tried many tips accross the web, but also passed on many that looked like they could break my sound completely again. 

If there's anyone here that has a good knowledge of sound in ubuntu I'de really appreciate some direction.


Also while i'm here, i have a second thing i'm tryin to resolve
within the il-2 (windows game), by copying the game files directly from a windows partition all settings were saved including my joystick controls, so the joystick actually works, which i'm excited about it. But there's one part that isn't working. This specific model has a HID (duhhh) --> (small mouse nub like we used to see on laptops in the 90's) Which i'de like ubuntu to recognize as an additional poining device and have active all the time, is this possible???

thanks, i hope i was clear on whats goin on

---

### Post by Groundswell on 2009-12-09
after 2 weeks a searching, i found something that has helped.

installing alsa-oss and running ts with aoss.

sudo apt-get install asla-oss

edit TS launcher by just adding aoss (aoss teamspeak)

teamspeak sound is fair now, and sound is available through the game now, however it is still laggy. sound is not available thru any other apps however.

---

### Post by rvndrk3233 on 2009-12-09
You can disable the very buggy and laggy pulseaudio and replace it with ALSA on up to 9.04.

9.10 has issues and this fix doesn't work. Its like one of the first few links if you google it.This fixes issues with skype as well.
Im running the beta.

---

### Post by Groundswell on 2009-12-09
I've tried that and it made all sound restrictive to one app at a time

---

