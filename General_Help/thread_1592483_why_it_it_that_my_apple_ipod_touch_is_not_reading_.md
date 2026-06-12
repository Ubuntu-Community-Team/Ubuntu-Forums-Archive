---
title: "why it it that my apple ipod touch is not reading on maverick meerkat?"
date: 2010-10-10
forum: General Help
---

### Post by demonspeedy on 2010-10-10
my apple ipod touch 4th generation is not reading as an mp3 player not at all t rather as a digital camera and i cannot for life of me put songs on it -because rythmbox music player is not reading it as well..... i have a compaq presario desktop model sr5507f and rythmbox music player -it should be showing upon the left hand panel an d its not there please someone add support for the apple ipod touch  4th generation on  maverick meerkat......   thanks many to who does correct this problem!

---

### Post by mcpish on 2010-10-15
I had this same problem when upgrading to 10.10 with my 5th generation iPod touch.  Worked perfect in 10.04, but wouldn't recognize in 10.10.  I figured it out and now have it working.

You need to re-install libimobiledevice1.  Open Synaptic and search for "libimobiledevice1", right click on it and choose "mark for reinstallation", click apply and let it install.  Then reboot your computer.  Worked perfect for me.

---

