---
title: "Musescore Sheet Music Generator: Crashes"
date: 2009-10-16
forum: General Help
---

### Post by asuastrophysics on 2009-10-16
Hey everyone,

I'm using this new software I just got called "Musescore" to compose some music. It seems to be working fine, up until I changed the time signature.

Is there a way to make this program more stable? It's greyed out right now and frozen, and I just lost 40 minutes worth of work...I knew this would happen.

These are the last outputs of terminal:
```
switch from EDIT to NORMAL
cmd <pad-note-4>
cmd <note-input>
switch from NORMAL to NOTE_ENTRY
Score::processUndoOp(i->type=RemoveElement, undo=0)
   Rest
   Score::removeElement 0x487a140 Rest parent 0x487a290 Segment
Score::processUndoOp(i->type=RemoveElement, undo=0)
   Segment
   Score::removeElement 0x487a290 Segment parent 0x4879ea0 Measure
Alsa_driver: stat = 00, xrun of at least 1255559184245.543 ms
Alsa_driver: stat = 00, xrun of at least 1255559184241.594 ms
Alsa_driver: stat = 00, xrun of at least 1255559183974.865 ms
Alsa_driver: stat = 00, xrun of at least 1255559184002.780 ms
Alsa_driver: stat = 00, xrun of at least 1255559184247.240 ms
Alsa_driver: stat = 00, xrun of at least 1255559184257.174 ms
Alsa_driver: stat = 00, xrun of at least 1255559184244.080 ms
Alsa_driver: stat = 00, xrun of at least 1255559184043.853 ms
Alsa_driver: stat = 00, xrun of at least 1255559184184.160 ms
Alsa_driver: stat = 00, xrun of at least 1255559183958.742 ms
Alsa_driver: stat = 00, xrun of at least 1255559184252.315 ms

```

I think the problem lies with Alsa, as you can see here it just decided to crap out. Does anyone know why or how I can prevent these XRUNS from happening, thus not loosing all my hard work? :(

Any help is appreciated :)

---

