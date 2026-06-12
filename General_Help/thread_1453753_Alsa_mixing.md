---
title: "Alsa mixing"
date: 2010-04-13
forum: General Help
---

### Post by sandyd on 2010-04-13
a) does my card support hardware mixing?
its a IDT 92HD73C1X5

b) if not, how can I activate software mixing? I can only play one sound at a time on my computer :(

---

### Post by kostkon on 2010-04-13
I don't believe so.

Very few cards still support hardware mixing and even fewer are the ones that their ALSA driver can use this feature.

If you use a vanilla Ubuntu, you already have a software mixer, i.e. PulseAudio. Even if you have removed it, ALSA provides its own simplistic software mixer (called dmix).

Thus, I believe the problem could be that some app tries to access your sound card directly instead of using dmix (or Pulseaudio for that matter), thus blocking your card and depriving the other apps of access to the software mixer (i.e. dmix or pulseaudio), or something like that.

---

