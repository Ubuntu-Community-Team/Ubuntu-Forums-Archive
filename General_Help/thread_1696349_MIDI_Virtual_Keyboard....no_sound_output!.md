---
title: "MIDI Virtual Keyboard....no sound output!"
date: 2011-02-27
forum: General Help
---

### Post by gabriella on 2011-02-27
Hi,

I just installed the MIDI Virtual Keyboard from the Software centre.
Problem is when I hit the keys there's no sound at all.

Please tell me what I'm doing wrong? or if I need to add some other package to make this work? 

Thanks!

---

### Post by gabriella on 2011-02-27
Any ideas?

---

### Post by jondodson on 2011-02-27
Hi.  The keyboard doesn't make any sound on it's own.  You need qjackctl and qsynth as well.  Open qjackctl first, then qsynth then vkybd.  Then go into the 'connect' option of qjackctl and hook up the inputs and outputs.  It sounds harder than it is.

Regards
Jon.

Ps you also need a sound font file (.sf2) for the synth.  You can get them online for free but I think there's one with 50 odd instruments in the standard ubuntu installation somewhere.  Can't remember exactly where though, do a search on your machine.

---

### Post by gabriella on 2011-02-28
> **jondodson said:**
> Hi.  The keyboard doesn't make any sound on it's own.  You need qjackctl and qsynth as well.  Open qjackctl first, then qsynth then vkybd.  Then go into the 'connect' option of qjackctl and hook up the inputs and outputs.  It sounds harder than it is.

Regards
Jon.

Ps you also need a sound font file (.sf2) for the synth.  You can get them online for free but I think there's one with 50 odd instruments in the standard ubuntu installation somewhere.  Can't remember exactly where though, do a search on your machine.

Thanks Jon.
That explains it then, knew it must be something basic I was missing.
Best, G

---

