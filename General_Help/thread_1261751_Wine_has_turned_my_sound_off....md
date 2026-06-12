---
title: "Wine has turned my sound off..."
date: 2009-09-09
forum: General Help
---

### Post by ricardino on 2009-09-09
Hi all, ive just installed wine on my Ubuntu 9.04, and ive tried to run a program under it. However it has now stopped all sound on my system. Not just for programs running under wine, but also my native linux programs. Ive gone into winecfg and there were no errors sent out. has anybody come across this problem before? 

thanks

---

### Post by SlugSlug on 2009-09-09
try a 

```
 sudo /etc/init.d/alsa-utils restart

```

---

### Post by ricardino on 2009-09-09
worked a treat. cheers

---

