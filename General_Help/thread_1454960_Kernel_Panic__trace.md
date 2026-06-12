---
title: "Kernel Panic / trace"
date: 2010-04-15
forum: General Help
---

### Post by Grenage on 2010-04-15
Greetings,

Does anyone have any experience with working out where a Kernel panic is coming from?  It's random, and I've ruled out memory; I thought it was a serial adapter driver, but it panics when I don't load it.  Personally, I can't see much useful information in there.

Attached are screenshots.

Edit: *hrtick_start_fair* could apparently be the cause, although I'm not yet sure how.  I'm disabling MRTG to see if it's reference is more than coincidence.

---

### Post by Grenage on 2010-04-26
It was a PCI slot issue, I just wish I'd figured that out *before* I'd reinstalled.

---

