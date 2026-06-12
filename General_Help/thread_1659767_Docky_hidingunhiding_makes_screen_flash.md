---
title: "Docky hiding/unhiding makes screen flash"
date: 2011-01-04
forum: General Help
---

### Post by JaredFactley on 2011-01-04
Reformatted computer and went from 32bit to 64. But when I installed Docky I had some problems I didn't encounter before.

First was even though I had compositing enabled, Docky didn't recognize it.

So I found other people with this problem and entered this command:

```
gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true
```

But this didn't fix my other problem. When Docky hides, or unhides it creates a bar that flashes across the screen. Here's a short video to explain what I mean:

[http://db.tt/YGtDS4w](http://db.tt/YGtDS4w)

Not sure if this is a problem with compositing or not, but I can't find anything about this anywhere. If anyone has any ideas, that'd be great.

---

### Post by Habitual on 2011-01-04
Docky version might help us help you... :D

---

### Post by JaredFactley on 2011-01-04
Of course, 2.0.10. I assume that's the latest? I just installed it through Synaptic.

---

### Post by JaredFactley on 2011-01-04
Well I didn't exactly fix this, but have made it work for me. 

For some reason it only happens when Docky is placed on the left side of the screen. Not top, bottom or right.

And it doesn't happen if it is set to fade on hide. Still not sure what is causing the problem but it's fine for me now fading away.

---

