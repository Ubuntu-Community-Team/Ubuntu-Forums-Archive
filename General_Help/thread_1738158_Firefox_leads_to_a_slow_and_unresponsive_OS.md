---
title: "Firefox leads to a slow and unresponsive OS"
date: 2011-04-24
forum: General Help
---

### Post by JamesPKing on 2011-04-24
This post refers to a computer with Ubuntu 11.04 installed, which has all the patches applied which were released before the time of writing this post. 

On opening Firefox the system immediately becomes slow and unresponsive. It takes a little while for the Firefox window to appear, and that is shaded out, signifying its unresponsiveness. 

The system monitor does not show a significant CPU or RAM usage at the time of opening or running Firefox, although it, and any other applications run as if RAM and CPU usage is near the maximum. 

Does anyone have any ideas about the cause or a remedy for this problem?

This is the 64 bit release, running on a Intel Core 2 Quad Q6600 with ~4GB of RAM.

---

### Post by balta on 2011-04-24
Maybe you have problems with Firefox itself, it could that you installed way too much addons or you have conflicting addons or a broken theme.
You should try firefox in recovery mode with the command:
> firefox -safe-mode
and check if it still unresponsive.
Maybe you could try to wipe out the installation and make a new clean install of firefox.
I'm sorry my knowledge stops here and I can't provide any further help or suggestions.

---

### Post by JamesPKing on 2011-04-24
> **balta said:**
> Maybe you have problems with Firefox itself, it could that you installed way too much addons or you have conflicting addons or a broken theme.
You should try firefox in recovery mode with the command:

and check if it still unresponsive.
Maybe you could try to wipe out the installation and make a new clean install of firefox.
I'm sorry my knowledge stops here and I can't provide any further help or suggestions.

Thanks:

I tried both suggestions, but I am still experiencing the same on that system (luckily it isn't mine ;) )... 

When I open TTY1 through n the console is spitting out lots of stuff referencing a disk sector that can't be read, I suppose this could be the root of the problem as the hard drive is very old. 

I think reinstalling Ubuntu on a different HDD will probably be the fastest way to solve this problem, unless anyone else has some other ideas?

---

