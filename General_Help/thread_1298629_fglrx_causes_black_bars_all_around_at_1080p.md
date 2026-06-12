---
title: "fglrx causes black bars all around at 1080p?"
date: 2009-10-23
forum: General Help
---

### Post by ghosthand on 2009-10-23
HI,  I have a vizio gv47lf 1080p televison hooked up to an ati 3600 graphics card.  When I use the free ati drivers everything works fine, and the picture fills the entire tv screen.  When I enable the proprietary drivers then everythig seems to work ok, but I get black bars around all the edges of the screen, as if the screen isn't stretched to fill the entire tv.  But the ati catalyst control center says its using 1080p.  I've tried fiddling with all the setting in the ati app, but nothing changes.  Is this an xorg modeline problem?  The strange thing is that the free drivers work just fine.

---

### Post by etnlIcarus on 2009-10-23
I found my 1920x1080 resolution didn't display correctly on my 1080p Samsung LCD television. For some odd reason, 16:9 mode on the *television* causes the edges of the screen to be cut-off, and the image to be up-scaled. Instead, I had to set it to, "Screen fit", which seems redundant but it fixed the problem (and I'm not going to argue with my TV).

In the television's options, make sure you've tried all the different screen fit/aspect ratio options.

---

