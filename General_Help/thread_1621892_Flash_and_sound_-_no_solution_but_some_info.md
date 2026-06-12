---
title: "Flash and sound - no solution but some info"
date: 2010-11-14
forum: General Help
---

### Post by squaregoldfish on 2010-11-14
There's a lot of threads knocking around regarding a lack of sound in Flash. I don't have a solution for this, but I do have a strange piece of information that may be relevant.

When I play a Flash thing with sound, I can't hear the sound in normal circumstances. However, if I start playing some music in Rhythmbox while the Flash is playing, suddenly I can hear the Flash sound. Weird.

This is on a 64-bit system, with the latest 64-bit Flash candidate.

I don't know if this gives any clues as to what might be happening, but I thought I'd share.

Steve.

---

### Post by yuki-nagato on 2010-11-14
> **squaregoldfish said:**
> There's a lot of threads knocking around regarding a lack of sound in Flash. I don't have a solution for this, but I do have a strange piece of information that may be relevant.

When I play a Flash thing with sound, I can't hear the sound in normal circumstances. However, if I start playing some music in Rhythmbox while the Flash is playing, suddenly I can hear the Flash sound. Weird.

This is on a 64-bit system, with the latest 64-bit Flash candidate.

I don't know if this gives any clues as to what might be happening, but I thought I'd share.

Steve.

sounds to me like flash isn't very good at piping the sound output to alsa/oss/pulseaudio like it should.  32 bit likely works a lot better at least until adobe hires a few more developers to fix things like this.

---

