---
title: "firefox 5 minute start up"
date: 2010-04-25
forum: General Help
---

### Post by winchendonsprings on 2010-04-25
As of the 3 days ago my main use firefox profile takes roughly 5 - 10 minutes to start.
Once it gets started it acts quick as usual. I don't believe it to be an extension because I haven't changed or upgraded any. 

No matter where I launch firefox from (gnome-do, docky, panel, directly from /usr/lib/firefox folder) it takes about 5-10 minutes. I have been starting it from the terminal "  firefox -p MainUse -no-remote  "

I have 3 other firefox profiles I use and they all start quickly on command.

any idea why this one takes forever to start or restart? or any tips? 

This doesn't seem to be the normal sluggish start some people have, i think, because after the alloted time it pops up and acts quick as usual.

---

### Post by lovinglinux on 2010-04-27
> **winchendonsprings said:**
> I have 3 other firefox profiles I use and they all start quickly on command.

That is your answer. Is probably an extension. Start Firefox with the command below:

```
firefox -safe-mode -P
```

Then select the problematic profile and disable all extensions. If it works, then enable the extensions one-by-one until you find the culprit. I would start with Cooliris, Prism, FoxTab...

---

### Post by winchendonsprings on 2010-04-28
Back to normal. I didn't update any extensions, I didn't update firefox, I just used a different profile for a few days then retried the problematic profile and all is well. strange.
I had a feeling it was something in my firefox files. but I don't care now

---

