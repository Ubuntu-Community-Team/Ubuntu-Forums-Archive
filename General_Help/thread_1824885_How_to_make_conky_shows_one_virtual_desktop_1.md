---
title: "How to make conky shows one virtual desktop 1"
date: 2011-08-14
forum: General Help
---

### Post by fjctp on 2011-08-14
Currently, my conky runs on both desktop, 1 and 2, but I just want it to run on the desktop 2 only. So how can I do it?

Thanks

---

### Post by Gillingham on 2011-08-14
I think I can help with part of your question.  I would guess that you are using sticky as one of the options in own_window_hints in your .conkyrc configuration file.  If you delete this then conky will appear on only one window.

---

### Post by fjctp on 2011-08-14
Thanks for your reply.
After removing "sticky" from own_window_hints, conky only shows on Desktop 1.
However, I want it on Desktop 2.
Therefore, I go to System Setting >> Window Behavior >> Window Rule and setup a new rule for window class: Conky.
Goto Geometry tab >> click the box next to Desktop >> force 2:Desktop 2
This works pretty good so far.

---

