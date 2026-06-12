---
title: "Can't get 32 bit applications to work on 64 bit Ubuntu 10.10"
date: 2011-11-04
forum: General Help
---

### Post by ingramproductions on 2011-11-04
I've ran this command:
```
sudo apt-get install ia32-libs
```
But whenever I try to install a 32 bit deb file, I always get error messages saying "Wrong architecture 'i386'"

Is there something else I'm supposed to be doing?

---

### Post by gsmanners on 2011-11-04
You could try

```
sudo dpkg --force-architecture -i mydebfile.deb
```

I suppose I'm obligated to warn that this could break your system, loss of data, etc. FWIW, it usually works.

---

