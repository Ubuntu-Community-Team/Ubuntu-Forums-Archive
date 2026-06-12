---
title: "No /dev/dsp"
date: 2012-08-07
forum: General Help
---

### Post by Sith Lord Kyle on 2012-08-07
I have a program for tracking audio on my computer, which worked fine a few days ago.  Now when I start it up it complains there is no /dev/dsp.

Looking in the /dev/ folder, there is indeed no dsp anymore.  How do I get that back?

UPDATE:  I have sound for everything else, so there is no sound issue... just no /dev/dsp

---

### Post by irv on 2012-08-07
Do you have **libbs2b0** Bauer stereophonic-to-binaural DSP library installed? I looked it up in the Synaptic Package Manager.
EDIT: If it is installed try to re-install it.

---

### Post by Sith Lord Kyle on 2012-08-07
> **irv said:**
> Do you have **libbs2b0** Bauer stereophonic-to-binaural DSP library installed? I looked it up in the Synaptic Package Manager.
EDIT: If it is installed try to re-install it.

I do have it installed, but I'll do sa re-install and see what happens.

UPDATE: Reinstalled but it didn't have any effect.

---

### Post by irv on 2012-08-07
By chance was it in the trash can?

---

### Post by Sith Lord Kyle on 2012-08-08
> **irv said:**
> By chance was it in the trash can?

Nope.  It was not.  Still can't figure this problem out.  There is literally nothing helpful doing a Google search nor can I find anything that works from the forum.

---

### Post by Sith Lord Kyle on 2012-08-08
Solved the problem myself...

The program was using Snack, TCL version, to play audio back and the person who wrote the program had included a line:

s play -device /dev/dsp -start

This plays the audio through Snack via /dev/dsp.  Since I have no /dev/dsp... maybe I never did, from what I read, I just deleted the -device /dev/dsp from the code.  Once I did that, the program just used what audio card I did have and it played fine!

I guess the /dev/dsp has something to do with OSS, which seems useless to me with newer Linux systems.

---

