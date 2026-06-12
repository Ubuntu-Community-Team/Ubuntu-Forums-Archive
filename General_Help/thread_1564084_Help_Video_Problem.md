---
title: "Help: Video Problem?"
date: 2010-08-30
forum: General Help
---

### Post by ngrieb on 2010-08-30
I thought this was a problem related to my attempt to tweak compiz to set the brightness on my laptop, but it seems as though it is something more than that after completely removing compiz it is still happening. 

I am experiencing some very odd video problems that I did not notice before, but I recently switched from 10.04 i386 -> 10.04 x64. My problem currently is that I cannot view local videos through totem, mplayer, banshee, etc. because all of the videos appear extremely bright...as in almost whited out. I have a Toshiba NB305 which has an integrated Intel N10 card in it. Does anyone know what is going on here?

I was able to finally get some terminal output when using mplayer:

open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.

When I tried the movies in Banshee they worked...anyone know why they have stopped working in the other players?

---

### Post by ngrieb on 2010-08-30
Sorry it appears as though the brightness and contrast in Totem were somehow altered...and awkwardly enough this affected every other movie player on my system as well. Who would have thought...
[SOLVED]

---

