---
title: "Same flac files, two different plot spectra?"
date: 2009-08-06
forum: General Help
---

### Post by nbtrap on 2009-08-06
When I first learned about flac, I began archiving my music losslessly, ripping my CDs to flac using Sound Juicer. I've since switched to a KDE desktop, and I was fooling around when I noticed that the same song ripped to flac has an ever-so-slightly different plot spectrum from what was ripped with Sound Juicer. Even when I decode the files to .wav, they are the EXACT same size, but Audacity is still giving me slightly different spectra. Doesn't this mean that either Sound Juicer or k3b is ripping to flac lossily, even if only a little bit? It's really bothering me, because I don't know which I should use.

---

### Post by nbtrap on 2009-08-06
After experimenting a little more, it seems Sound Juicer and k3b are giving me the exact same flac files now. I don't know why/how, but for some reason, the music I ripped a couple months back is slightly different from what I'm getting when I rip now. Could this have something to do with my old CD drive I had replaced after it gave me problems?

---

### Post by CatKiller on 2009-08-06
Just a thought; If you had a normalising step in your pipeline when you were ripping them before then you may get slightly different spectra (the track would be ever-so-slightly louder). I have no idea if any of the tools have ever included a normalising step by default.

If you feel like playing, taking the difference between the two versions (one minus the other, or one plus a phase-inverted version of the other) might point you to what the change was. Or it might not. Or it might be too dull to bother with :)

---

### Post by nbtrap on 2009-08-06
It doesn't look like they do, though Sound Juicer may have at some point. And it does look like one track is slightly louder (the spectrum plot is slightly higher all-around). Can normalizing the tracks with a lossless encoder ever cause clipping? If so, is there a way to undo normalization?

---

### Post by CatKiller on 2009-08-06
> **nbtrap said:**
> Can normalizing the tracks... ever cause clipping? 

Yes, sometimes. RMS rather than peak normalisation could do this.

> If so, is there a way to undo normalization?

In some cases; if you knew what the gain applied was, and there wasn't any clipping.

---

### Post by nbtrap on 2009-08-06
As far as I can tell, the only way to normalize volume with the flac encoder (and not the Gstreamer flac encoder) is with --replay-gain. This option is not enabled in k3b, so am I correct to assume that I don't have to worry about it when ripping with k3b?

---

### Post by CatKiller on 2009-08-07
Actually, flac's --replay-gain option doesn't do anything to the audio. It only writes tags.

But you said that you were using Sound-Juicer to rip the problematic files, and that **does** use GStreamer. It's possible that one of the pipeline elements had a (deliberate or not) normalising function at some point in the past.

Personally, I'd either re-rip the tracks that you ripped before or just forget about it.

---

