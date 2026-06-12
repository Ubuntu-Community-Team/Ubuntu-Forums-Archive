---
title: "Grub doesn't load because of 2nd (faulty) HD in Karmic"
date: 2009-11-01
forum: General Help
---

### Post by Logan 1229 on 2009-11-01
Here's an interesting scenario I wonder if anyone has encountered.  I did a fresh install of 9.10 on computer with a single HD.  All minor problems got solved.  

  Backed up a faulty 2nd HD (externally).  Note: If drive is connected as master, it boots fine.  Determined it was failing by using smartmontools (& because it was taking so long to do stuff).  Tried to format externally but failed, so I installed it internally to do so.  Reason: trying to recover bad sectors to see if HD still has some life or if it needs to go to HD heaven.

  Now this is where it gets interesting.  Computer with freshly installed, working Karmic tries to load Grub but freezes up.  I made sure boot order, cabling, jumpers, etc, were all correct (even tried some non-correct configurations for fun).  Note, though, that this 2nd HD has 9.04 on it (not sure why it should matter though if I'm connecting as a slave to wipe clean & format).  I actually had to disconnect the 2nd HD from the computer before Grub would load.  Then everything works fine.

  Ideas anyone? Not sure if this is a bug or just me doing something incorrect.

---

