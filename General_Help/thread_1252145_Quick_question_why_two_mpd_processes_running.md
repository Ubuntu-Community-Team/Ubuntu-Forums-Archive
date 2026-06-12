---
title: "Quick question: why two mpd processes running?"
date: 2009-08-28
forum: General Help
---

### Post by treehouse on 2009-08-28
I had to reinstall mpd after a fresh Ubuntu install and it starts at startup, and runs as my username. Top tells me that I have two instances of mpd running that stay really close to eachother as far as resource usage and are both running as my username (not root or 'mpd' or anything else).

Why two instances instead of one?

---

### Post by DefineByte on 2009-09-05
I believe mpd currently uses multiple processes in lieu of multiple threads. It's perfectly normal. :)

---

