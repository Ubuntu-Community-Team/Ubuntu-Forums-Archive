---
title: "'apt' (dpkg) and 'apt' (java)"
date: 2010-09-09
forum: General Help
---

### Post by luigi_mb on 2010-09-09
Synaptic indicates 'apt' (front-end for dpkg) is installed in /usr/bin . However what is actually in /usr/bin is a symlink 'apt -> /etc/alternatives/apt' which ultimately points to 'apt' (annotation processing tool), a component of Sun Java. 

Frankly I do not know wether the symllink to Sun's apt is necessary, in which case I could delete it and re-install apt (dpkg). 

Any advice?


/luigi

---

