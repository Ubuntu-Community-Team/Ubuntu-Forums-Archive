---
title: "Restoring  desktop behavior"
date: 2012-05-20
forum: General Help
---

### Post by risotto77 on 2012-05-20
Hi.

I want to restore my default Unity desktop behavior after messing with compis settings. Well at least I want three functions back. Taht is 1) maximize window when I drag window to top edge, 2) make window occupy left part of screen when I drag window to left edge, 3) make window occupy right part of screen when I drag to right edge. I do not know why I lost this functionality, but I want it back.

So far I have tried:
- messing with lot of options in ccsm
- gconftool-2 --recursive-unset /apps/compiz-1
- gconftool-2 --recursive-unset /apps/compizconfig-1
- unity --reset (segfaults)

I also logged out and in to a guest session and this functionality was not there either. Making me think there is a problem with system configuration rather than user configuration. Or I am going insane and I never really had this functionality. Please help me.

---

### Post by risotto77 on 2012-05-26
poke

---

### Post by stinkeye on 2012-05-26
Check your in the **Ubuntu** session...
```
echo $DESKTOP_SESSION
```

In the terminal...
```
unity --reset & disown
```
should load the default compiz settings.

The window resizing when moved to the edge is controlled by the ccsm grid plugin.

---

### Post by risotto77 on 2012-05-26
Thank you for advice. Got a segfault with that unity --reset. Looks like there is a problem with the unfree fglrx drivers for ati. Changed back to the free ati drivers and all is good now :-) . Better stay free I guess.

---

