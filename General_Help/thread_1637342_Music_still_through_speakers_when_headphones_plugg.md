---
title: "Music still through speakers when headphones plugged in."
date: 2010-12-04
forum: General Help
---

### Post by h34e0f on 2010-12-04
As title. Managed to get it to play through both simultaneously but can't make the laptop speakers stop when the headphones are plugged in...

---

### Post by krishnandu.sarkar on 2010-12-04
Go to Sound Preferences(From sound applet or System > Preferences > Sound), go to Output tab, now select only Headphone

---

### Post by h34e0f on 2010-12-04
Then it doesn't work when I unplug the headphones... or is it a case of changing over whenever I change my hardware?

---

### Post by bluelamp999 on 2010-12-04
> **krishnandu.sarkar said:**
> Go to Sound Preferences(From sound applet or System > Preferences > Sound), go to Output tab, now select only Headphone

Yes, but that kills the speakers.

I think the OP means that when you plug in headphones, the speakers should automatically mute...

---

### Post by h34e0f on 2010-12-04
exactly, is this possible? one would expect this to be standard practice

---

### Post by bluelamp999 on 2010-12-04
> **h34e0f said:**
> exactly, is this possible? one would expect this to be standard practice

Indeed one would...

On my new desktop, auto muting of speakers doesn't happen when headphones are plugged in.

I've been too lazy to check out why (I just turn down the speakers!) but it would be nice to know...

---

### Post by h34e0f on 2010-12-04
Well my problem is it's a laptop so can't turn down speakers. I'll keep searching for a way around it! Thanks

---

### Post by bluelamp999 on 2010-12-04
For what it's worth, it looks like this is a 10.10 bug - [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/653737](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/653737)

---

### Post by Mad-Halfling on 2010-12-05
The odd thing is (it being a known 10.10 bug) was that I have this on my new laptop with 10.10 but not on my old laptop, which also had 10.10

---

### Post by psihokiller4 on 2010-12-05
in 10.04 I found it same but if I go to:





step 1:
I plug in headphones

step 2:
System --> Preferences --> sound --> hardware(tab)

Internal Audio --> profile (off)

step 3:
System --> Preferences --> sound --> hardware(tab)

Internal Audio --> profile (on)




and it's switched my seekers doesn't output sound any more
that's how I have to do it in 10.04

---

### Post by IndyGunFreak on 2010-12-05
> **Mad-Halfling said:**
> The odd thing is (it being a known 10.10 bug) was that I have this on my new laptop with 10.10 but not on my old laptop, which also had 10.10

I believe it's specifically related to Intel HDA chipsets, but I thought there was a fix(at least I fixed it on my laptop... just can't remember how)

---

### Post by bluelamp999 on 2010-12-05
So can anybody help here?

I've just fired up Windows on my machine and plugging in the headphones mutes the speakers.

How can I achieve this in 10.10 64 bit?

---

### Post by bluelamp999 on 2010-12-06
Gentle *bump* here...

This is becoming annoying.

I've installed the various ALSA front ends *alsamixergui, ALSA Mixer and GNOME ALSA Mixer* looking for jack-sense (or something like that) but to no avail...

There must be a fix (this *is* Ubuntu after all) - can anyone please help?

Thanks

---

