---
title: "esd and system sounds problem"
date: 2004-10-19
forum: General Help
---

### Post by Nikola on 2004-10-19
I have problems with system sounds. It looks like esd is failing, no sound on system events.
Error is like this:

```
/usr/bin/esd&#58; relocation error&#58; /usr/bin/esd&#58; undefined symbol&#58; esound_getblksize
```

Alsa and oss works OK, but only esd fails. BTW, why system sounds use esd, but not alsa? Alsa should be standard for Gnome, right? But now I have oss, alsa and esd.

---

### Post by iwasbiggs on 2004-10-19
I can't help with your first question, but I can with the second.

ALSA standard for gnome? Not really. ALSA is just the new sound system for the kernel. Naturally, until all OSS applications are cleaned up for ALSA, ALSA will still provide legacy OSS devices.

The current sound daemon (esound) is still the solution for most gnome applications to make noise. By Gnome 2.10 applications should favor the gstreamer solution (which can have multiple backends: ALSA, OSS, esound, jack, arts, etc.)--at least that's the idea I think.

---

### Post by Nikola on 2004-10-20
Solved it by upgrading esound, works ok now.  :D

---

