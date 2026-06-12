---
title: "Evolution Mail Crash"
date: 2011-02-04
forum: General Help
---

### Post by Thonixx on 2011-02-04
Hi it's my first thread here, but I hope you can help me.

I use Evolution for mail, contacts and calendar. If I am browsing through my calendar and going too far in the "future" of my appointments and then clicking the "Today" button, Evolution crashes.
What can I do at this point? It's annoying.

Thanks for answers,
Thonixx

---

### Post by [Snc] on 2011-02-04
> **Thonixx said:**
> Hi it's my first thread here, but I hope you can help me.

I use Evolution for mail, contacts and calendar. If I am browsing through my calendar and going too far in the "future" of my appointments and then clicking the "Today" button, Evolution crashes.
What can I do at this point? It's annoying.

Thanks for answers,
Thonixx

Welcome to the forum!

Can you launch it from the terminal, then make it crash and post back the results?

---

### Post by Thonixx on 2011-02-05
> EI: MAIL PREFS**
Gdk:ERROR:/build/buildd/gtk+2.0-2.22.0/gdk/gdkregion-generic.c:1110:miUnionNonO: assertion failed: (y1 < y2)
AbortedThat's all..

And the following if I click too fast on "Today" when I changed date.
> EI: MAIL PREFS**
Gdk:ERROR:/build/buildd/gtk+2.0-2.22.0/gdk/gdkregion-generic.c:1189:miUnionO: assertion failed: (pReg->numRects<=pReg->size)
Aborted

---

### Post by dcstar on 2011-02-06
> **Thonixx said:**
> Hi it's my first thread here, but I hope you can help me.

I use Evolution for mail, contacts and calendar. If I am browsing through my calendar and going too far in the "future" of my appointments and then clicking the "Today" button, Evolution crashes.
What can I do at this point? It's annoying.


I cannot duplicate this behaviour on my 10.04 or 10.10 test systems.

Report it as a bug as certain Calendar entries can cause issues:

```
ubuntu-bug evolution
```

---

### Post by Thonixx on 2011-02-06
I have to correct my statement to the problem.
I can crash Evolution if I click on the symbol of next week (the button which shows me the following week) continously and then fast clicking on the "Today" button then evolution crashes.
If I wait a few seconds then it doesn't crash.

I sent the bug how you said, thanks for helping. How long do you think does it take to remove this bug?

---

