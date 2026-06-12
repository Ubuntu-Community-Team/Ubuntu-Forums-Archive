---
title: "No sound??"
date: 2009-10-25
forum: General Help
---

### Post by dbyjazz on 2009-10-25
My sound is not working and I've tried everything I can think of. I've provided screen shots.

I don't know if this is a Karmic Koala problem or not.

---

### Post by rockstarrem on 2009-10-25
Where's the screenshots? Oh, nevermind, didn't load. 

Have you gone to System > Preferences > Sound and tried out different cards there?

---

### Post by P4man on 2009-10-25
try installing gnome-alsamixer. Then make sure channels like PCM or surround are not muted.

---

### Post by dbyjazz on 2009-10-25
> **P4man said:**
> try installing gnome-alsamixer. Then make sure channels like PCM or surround are not muted.

did that

---

### Post by P4man on 2009-10-25
I take it you already tried unchecking IE958 as well?
What sound card do you have ?

**edit:** hang on: is that a second sound card on the other tab ? The thing ending in AGR ?

---

### Post by dbyjazz on 2009-10-25
> **P4man said:**
> I take it you already tried unchecking IE958 as well?
What sound card do you have ?

**edit:** hang on: is that a second sound card on the other tab ? The thing ending in AGR ?

what about IE958?

here's my output:

```
description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:1000(size=256)
```

edit: I'm pretty sure it's for calling people. ie stuff I won't use. It says 'caller id' etc.

---

### Post by P4man on 2009-10-25
> **dbyjazz said:**
> what about IE958?



Uncheck it. Its for optical audio out afaik and it seems selected. At the bottom of alsa mixer.

---

### Post by dbyjazz on 2009-10-25
> **P4man said:**
> Uncheck it. Its for optical audio out afaik and it seems selected. At the bottom of alsa mixer.

k I unchecked it. I'm trying to hear audio through websites like playlist.com. Should I just try a sound check for now? And I forgot how to do that in terminal..

does this all look normal??

---

### Post by P4man on 2009-10-25
try playing some music in rhyhtmbox or something, as not having sound in firefox/flash could be an entirely different issue (and a common one for that matter)

---

### Post by dbyjazz on 2009-10-25
didn't work :/

---

### Post by P4man on 2009-10-25
googling on your audiocard and ubuntu karmic, the only problems I find is people not having their speakers plugged in or accidentally muted volume. Are you sure you're not overseeing something trivial like that?

Im running out of ideas, but perhaps try running (if needed installing) pavucontrol. See if at least you see a volume bar moving if you're playing music. See if you can move the stream to the internal audio..

---

### Post by dbyjazz on 2009-10-25
> **P4man said:**
> googling on your audiocard and ubuntu karmic, the only problems I find is people not having their speakers plugged in or accidentally muted volume. Are you sure you're not overseeing something trivial like that?

Im running out of ideas, but perhaps try running (if needed installing) pavucontrol. See if at least you see a volume bar moving if you're playing music. See if you can move the stream to the internal audio..

got it working! just changed the connector

thank you so much for helping me

---

### Post by P4man on 2009-10-25
Doh!
Oh well, glad it works now :) Dont forget to mark the thread as solved.

---

### Post by dbyjazz on 2009-10-25
Awesome, will do!

---

