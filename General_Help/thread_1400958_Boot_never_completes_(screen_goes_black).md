---
title: "Boot never completes (screen goes black)"
date: 2010-02-07
forum: General Help
---

### Post by recyclist on 2010-02-07
This is my first post to this forum. 

Because...I have had a really bad day (the first, after months of faultless operation)) with my Acer 5720Z laptop running Ubuntu 9.04 Jaunty. First thing was at the second startup today, nothing other than totally black or white screens showed during boot. However, the ubuntu jingle was heard after the normal time it takes to boot, so I was certain it was strictly some video problem.

 Ok, so after having thought about this for a while and reading about similar issues here and there on the web I was struck by the fact that not even the Acer screen with bios info etc. showed normally just after power-up. By then I had dragged a second, stationary computer to the livingroom, so I thought I'd check if there'd be video output from the Acer's VGA port. There was, and the ubuntu desktop looking perfectly normal. Aha! - only the backlight working on the Acer's LCD screen, but no video? So I thought I'd check for loose connectors to the LCD or damaged wiring (installed replacement LCD myself some months ago with no problems). This is going to be easy, I thought (being more of a gearhead/hardware type of guy) Turned the Acer laptop off and unscrewed the screen frame stuff. Now I just start it and switch back to internal display... For some reason (too many unclean shutdown(s) during the early "blind" nervous phase of the problem, I suppose) the Acer now hangs with a black screen before boot is complete and I am unable to switch between external/internal monitors. Fortunately I can use the external monitor (video is stuck to the external VGA on startup), get to command prompt etc. so there should be hope. But I have no idea how to sort this out after many unsuccessful attempts. (Recovery mode, disk check etc.)

 I can't find any sort of safe graphics mode option in the GRUB menu. **Booting from the Ubuntu 9.04 ("live" option) also finally stalls with a black screen and nothing further happening, just like the install that's on the PC. **

 I'm not sure how to produce the log detailing possible errors or how to get it across to a working computer for posting here so I would be needing detailed instructions if anybody would be kind enough to help. I'm simply not enough of a wiz to figure this out myself.

 In the mean time I'll be getting an idea of how Ubuntu 9.10 runs on a stationary HP Pavillion 1840 which I rescued from the trash just like the Acer laptop.

Thomas 

(Norway)

---

### Post by recyclist on 2010-02-07
OK, an update:

 Of course, a little later I found the safe graphics mode option when booting from the CD. (And only when booting from the CD!) Starting a live session from the CD works with safe graphics mode, otherwise not. Booting from the HD in safe graphics mode (at least that's what I tried to do) results in the aforementioned black screen boot failure. Since I had a 9.04 install that I was really happy with, and with quite a bit of time spent tweaking and installing useful stuff, I really really want to get this install restored to its proper working condition. It would save me a huge amount of work and hassle.  Since I can't seem to find a way to boot into the installed system, I guess anything that can be done has to be done from the command prompt before loading ubuntu.  

 Still hoping somebody can help...

Thomas

---

