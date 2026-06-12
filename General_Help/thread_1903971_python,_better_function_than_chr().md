---
title: "python, better function than chr()?"
date: 2012-01-03
forum: General Help
---

### Post by d3v1150m471c on 2012-01-03
i have an array of integers, each item ranges from 0-255, and i need to convert them to ascii characters. problem is python's chr() is extremely slow when you're working with a large array. an array of 200kb's takes over 10 seconds to convert and this is useless. anyone knows of a faster function to do this?

---

### Post by d3v1150m471c on 2012-01-03
false alarm, apparently the problem was actually 'cython' and not python, much to my surprise.

---

