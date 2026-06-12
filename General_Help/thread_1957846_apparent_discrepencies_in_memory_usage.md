---
title: "apparent discrepencies in memory usage"
date: 2012-04-13
forum: General Help
---

### Post by Thorsen V on 2012-04-13
I wonder if someone can clue me in to the apparent discrepancy I see in memory usage on my 10.04 machine using different tools:

If I use*** gnome-system-monitor*** it reports[INDENT][FONT=Courier New]Memory[/FONT]
[FONT=Courier New]451.5 MiB (23.2%) of 1.9 GiB[/FONT]

[FONT=Courier New]Swap[/FONT]
[FONT=Courier New]0 bytes (0.0%) of 3.3 GiB[/FONT]
[/INDENT]Yet ***top*** shows:[INDENT][FONT=Courier New]Mem:   1991168k total,  1388464k used,   602704k free,   184340k buffers
Swap:  3485688k total,        0k used,  3485688k free,   739684k cached
[/FONT][/INDENT]***free*** generates similar numbers to ***top***.

Basically much higher used levels than does [B][I] gnome-system-monitor.

[/I][/B]I don't suppose it's anything to worry about but it does seem odd to me.

---

### Post by Habitual on 2012-04-13
This may shed some light on this:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Thorsen V on 2012-04-13
> **Habitual said:**
> This may shed some light on this:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
I see. I think I was confusing cache with swap.

Thanks for your help.

---

