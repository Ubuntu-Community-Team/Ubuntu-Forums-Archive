---
title: "Ubuntu crashed - sort of"
date: 2009-08-08
forum: General Help
---

### Post by bondmatt on 2009-08-08
I was using Octave to integrate over about a million points (literally) when all of a sudden the screen went dark for a moment, the Nvidia boot screen came up, and Ubuntu prompted me to log in (not a full restart, more like logging out and then asked to log in). I did not log out. I was also watching processor temperature closely. What gives?

The data I was integrating is essentially the same repeating cycle over and over again (pressure volume trace from an HCCI engine). Did Ubuntu look at what Octave was doing and decide that it looked like an infinite loop?

I intend to break down the data systematically before integrating anyways which should prevent this from happening again. I was only integrating the entire data set out of curiosity (I was unsure of my previous processing and the function I was calling up to integrate).

Thanks,
- engineering student

---

### Post by P4man on 2009-08-09
sounds like X crashed on you. Its certainly not because ubuntu 'thought' it was an infinite loop. Check your log files for any errors (system > administration > log files) it may help give a clue as to what happened.

---

