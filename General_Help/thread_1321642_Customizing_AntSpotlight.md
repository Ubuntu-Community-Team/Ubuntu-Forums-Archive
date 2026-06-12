---
title: "Customizing AntSpotlight"
date: 2009-11-10
forum: General Help
---

### Post by teh603 on 2009-11-10
Anyone know how to change the pictures in the AntSpotlight screensaver? I tried adding and removing pics /usr/share/backgrounds , but all that did was make the ant walk over an ugly test pattern and make Nautilus scream about its hash table. I'm running Jaunty, and I'm sick of the usual photos from the space shuttle.

Already tried google, and it doesn't seem to be of much help.

---

### Post by teh603 on 2009-11-10
Solved, and will be adding the [solved] tag to it as soon as I figure out how. Aparrently, everything in /usr/share/backgrounds has to have read only permissions set for the group root and everybody else, not just read and write for the root user and nothing for everybody else.

---

