---
title: "PrntScrn Opens RhythmBox"
date: 2009-09-23
forum: General Help
---

### Post by iEthan on 2009-09-23
As the title says, when I hit PrntScrn, instead of the Screenshot dialog opening, Rhythmbox does.

What's going on here?

---

### Post by Compintuit on 2009-09-23
The keyboard shortcut for launching rhythmbox could have been changed to printscreen. Open keyboard shortcuts, choose sound, and find "launch media player" Give it a new shortcut, if it was a print before. That may or may not work. Also, if you could give the output of xev that would be great.
open a terminal, type xev, hit printscreen, then close the box that appeared. There are a lot of things that could be causing this.

---

### Post by iEthan on 2009-09-23
The first thing did the trick. Thanks!

---

