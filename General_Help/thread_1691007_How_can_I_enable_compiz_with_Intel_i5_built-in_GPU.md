---
title: "How can I enable compiz with Intel i5 built-in GPU"
date: 2011-02-19
forum: General Help
---

### Post by chrroessner on 2011-02-19
Hi,

I have an Intel i5 that can do graphics and I thought I could safe energy, by taking out my ATI 6850, which I normally only use under Win 7, if doing some games. And this has become very rare :-)

So in fact this is a workstation. I enabled the graphics in the bios and it boots okay. X starts (after disabling fglrx stuff in xorg.conf).

But no compiz. But unfortunately I need this really for my eyes, because it has the neg plugin! And I am not going to use any other bad workaround, as neg is the only one that works for me.

My guess is that composition is available, because avant-window-navigator works perfectly (guess it would not work without, right?).

So does the i5 have indirect rendering? If so, how can I enable this in xorg.conf or elsewhere?

By the way: I am talking about Maverick here ;-)

EDIT:
switching from Maverick to Natty makes the iGPU work.

Thanks in advance
Christian

---

