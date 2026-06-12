---
title: "Installed Sorune, Not There"
date: 2009-07-20
forum: General Help
---

### Post by mikelmahoo on 2009-07-20
I installed sorune with synaptic. It does not appear below sound and video. How do I open it?

---

### Post by kk0sse54 on 2009-07-20
Open up a terminal and type 

```
man sorune
```

in order to see all the options available when starting sorune. Seeing that the gui is started by default you might be able to just start it also by pressing Alt + F2 and typing in "sorune".

---

### Post by mikelmahoo on 2009-07-20
Turns out Synaptic didn't add all of the dependencies, because I needed the Perl-tk module for it to open.

---

