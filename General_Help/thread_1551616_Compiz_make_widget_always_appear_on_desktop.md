---
title: "Compiz make widget always appear on desktop?"
date: 2010-08-12
forum: General Help
---

### Post by h4x0rmx on 2010-08-12
I just installed conky, but I had to make it a widget inside compiz so I can only see it when I hit F9. (I had to make it a widget because it conflicted with some compiz settings).
I was wondering if there's a way to make my widget sticky?
I know there are some windows rules on compiz, but I can't get the widget to always stay on.
Any suggestions?

---

### Post by Zorgoth on 2010-08-12
> **h4x0rmx said:**
> I just installed conky, but I had to make it a widget inside compiz so I can only see it when I hit F9. (I had to make it a widget because it conflicted with some compiz settings).
I was wondering if there's a way to make my widget sticky?
I know there are some windows rules on compiz, but I can't get the widget to always stay on.
Any suggestions?

I've never had a problem with "sticky" - the Window Rules plugin of compiz should handle that - just grab the Window class or some other property (using the green plus in ccsm to the right of "Sticky") and put something like "class=Conky" in "Sticky" in Window Rules in ccsm.  You can also give it lots of other traits.

By "sticky," you mean it should appear on all workspaces?  Because that is what it means - always on top is "Above" in Window Rules, which will work for most things but sometimes not with other windows that are also always on top (e.g. guake).

---

### Post by h4x0rmx on 2010-08-12
It isn't working for me! :(

---

