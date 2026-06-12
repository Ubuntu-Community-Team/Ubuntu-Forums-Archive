---
title: "PyChess: Holy Pegged CPU Cores, Batman."
date: 2011-06-21
forum: General Help
---

### Post by Krovas on 2011-06-21
When I run PyChess, python maxes out both of my lappy's cpu cores. It's not even playing that challengingly. What's up with that?

---

### Post by urmomsgoat on 2011-12-18
It's not playing challengingly because you're probably playing against the built-in python engine which is not yet a strong engine. Install stockfish and play against that if you want a challenge.
# sudo apt-get install stockfish

Currently their is no way to control how much CPU your engine uses; it is set to the lowest CPU priority though, so it shouldn't interfere with normal desktop operations (not including CPU intensive things like video decoding, etc.). When you close a game's tab it should kill the analysis engine and therefore the CPU usage.

---

