---
title: "Sound delay in games"
date: 2006-03-29
forum: General Help
---

### Post by Anessen on 2006-03-29
Hello there
I have a problem, sound (especially noticable in games) is delayed by about half a second. I have a Soundblaster Audigy LS with an Asus P4S800D motherboard that should have it's onboard sound disabled in the BIOS. I am using ALSA as a sound output, nothing else seems to work with the games.

Things I have tried:
Creating .asoundrc in my home directory, and filling it with:
```
pcm.0 {
	type hw
	card 0
}

ctl.0 {
 	type hw
	card 0
}

```
This should reference the first card on the system, yes? Well, if I do this, my card stops showing in Sound Preferences, and the delay is still there.

I have also tried modifying the asoundrc.conf file in /etc/, and filling it with the above. No difference at all.

I have had this problem before on another distro, but didn't get a chance to fix it before switching. This is not a problem caused by general slowdown. I get the problem on very simple games too.

---

### Post by Anessen on 2006-03-29
What is the possibility that this is a problem with my motherboard or soundcard? As in, an incompatability. I read somewhere that there was limited support for the P4S800D.

---

### Post by Anessen on 2006-03-29
Sorry to bump this up again, but I have found that my sound card is sharing IRQ16 with my ethernet card (cable modem). I remember that this used to cause problems for some people under windows, is the same true of Linux?

EDIT for what it's worth, I have exactly the same problem with the onboard sound enabled.

---

