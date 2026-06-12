---
title: "Display Crash?"
date: 2010-08-02
forum: General Help
---

### Post by Flexico on 2010-08-02
OK, this seems to happen sometimes (most of the time) when the display setting change, i.e. when starting a full-screen program or switching from text-screen-mode to image-screen-mode at boot. (I don't know what to call it other than "...-mode".)

I can tell that things still happen as if everything was fine, but there's no picture. I tried booting from the LiveCD, but THE SAME THING HAPPENS before anything even shows up, beyond "ISOLINUX yadda yadda booting up ... " and a flashing cursor.

This happened in Ubuntu 8.10 Intrepid Ibex, a little less often than Windows XP gave me the Blue Screen of Death ... and that's not very often; XP is very well-behaved under my command. ^^ Anyway, I upgraded to 10.04 Lucid recently because it's LTS and Intrepid just suffered End Of Life, and it's been doing this CONSTANTLY!

I think it has something to do with display drivers; I have an integrated ATI card 256MB and 401 MHz. That sounds good to me, especially considering my laptop's 3 years old, but I'm not sure.

---

### Post by Flexico on 2010-08-02
Oops, forgot to post the images!

---

### Post by fragos on 2010-08-03
I've seen this with 10.04 2 or 3 times. I'va a Nvidia GeForce 7050 PV on my motherboard and run the Ubuntu recommended video driver nvidia-current which is currently 195.36.24. It's happened so infrequently That I haven't recognized a pattern in my use that might relate to the issue. I hit the reset button when it happens and it reboots to normal operation. Would seem like the issue is in X or the driver but I'm just guessing.

---

### Post by Flexico on 2010-08-04
Thanks. Anyone else have a clue as to a solution?

_**Update:**_
OK, I managed to boot up the Install CD all right, and re-installed Lucid fresh -- everything seemed to be fine for a couple days as I re-installed all my favorite programs, but then my laptop overheated and blinked off (a secondary problem I'm working on) and after the "unclean shutdown", it happens every time I try to boot Ubuntu! Even from the LiveCD!

The fact that it affects separate boot disks the same way makes me think there's something in the hardware or BIOS, but I have no idea what it could be.

---

