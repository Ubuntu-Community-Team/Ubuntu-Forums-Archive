---
title: "Anybody out there run Audacious over an iec958 device?"
date: 2011-07-25
forum: General Help
---

### Post by mikeydeeeee on 2011-07-25
I've been trying to get Audacious (or any sound player, really) to run reliably over the s/pdf port on my Envy 24 compatible sound card.  I do this by selecting the alsa output drivers in Audacious and using them to open the iec958 device directly.

The idea here is to send the high quality sound output (like video and music) to my stereo system while leaving the lower quality stuff (like system sounds, web page output, etc) coming through my desktop speakers.  Sounds reasonable, right?

Problem is that for no reason I can determine, Audacious comes back with a 'pcm_hw' device busy error, when the mood hits it.  Weird thing is, it only happens for some songs.  Some songs always play regardless of the system state, which leads me to believe that the error's somewhere in Audacious, not alsa or the rest of the system.  Sometimes it works fine, but lately not at all.

So, does anybody else have any experience with this kind of setup?  Anybody have any ideas?

---

