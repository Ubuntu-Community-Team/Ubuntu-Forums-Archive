---
title: "Setting global copy/past as windows+C/V (gconf or keyboard shortcuts)"
date: 2010-07-20
forum: General Help
---

### Post by wahr on 2010-07-20
I've been reading up on this and there just isn't much literature.

I pair off between web browser, gedit, and shell often, and am looking to set global keyboard copy/paste shortcuts to win (Mod4) + C and V instead of ctrl+c/v, overriding the app defaults.

Attempting to add a new shortcut through the graphic "keyboard shortcut" menu produces a request for a command (research shows this is part of gtk at the global level, though there isn't much more on it, or if it can even be called at a higher level than compile time source)

Attempting to edit through gconf editor causes problems.. first off, simply adding the entry does not produce the schema, and second, gconf editor does not have full schema edit support.  

Anyone have experience with this and know how I might go about getting it done. I don't like the idea of mucking about with manual configs without a few hints at least to avoid really messing something up.

---

