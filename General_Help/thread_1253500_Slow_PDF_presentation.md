---
title: "Slow PDF presentation"
date: 2009-08-30
forum: General Help
---

### Post by matija on 2009-08-30
Hello.

I often use PDF for giving presentations and there are some performance issues that bother me. To be more precise: when there are large figures (images) on a page (slide), it takes up to one second to switch to that slide if viewing in full-screen (evince calls that mode 'presentation') mode. This is true for every single viewer I have tried (evince, xpdf, okular, acroread, impressive).

If switching slides would be slow in a non-fullscreen mode, I would have accepted that it's just not possible to do it faster. But as evince is able to switch **momentarily** when not in presentation mode (yes, also in its 'full-screen' mode, where it still shows a toolbar), so holding PageDown key moves fluently through all the slides, I believe it should work like that in presentation mode too.

I am therefore interested if there is anyone that has solved this problem or at least can explain what is happening behind-the-scenes.

By the way, I experience this problem on both of my computers; one of them has ATI Radeon (with fglrx driver) and the other one has an Intel i915 (using "intel" driver). Replacing compiz with metacity ("metacity --replace") doesn't make a difference.

Thanks in advance for any answers!

---

### Post by Liolikas on 2009-08-30
Try proprietary radeon driver.

---

