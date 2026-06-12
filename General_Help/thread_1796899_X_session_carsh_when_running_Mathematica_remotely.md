---
title: "X session carsh when running Mathematica remotely"
date: 2011-07-04
forum: General Help
---

### Post by muadnu on 2011-07-04
I'm using Ubuntu 11.04 and trying to run Mathematica remotely. After doing ssh -X to the remote machine and running Mathematica (setting fonts correctly) my X session crashes. Doing the same (with the same remote machine) with in Fedora 14 works with no trouble. 

I've read suggestions of running
```
env XLIB_SKIP_ARGB_VISUALS=1 mathematica
```
though this was for local installations of Mathematica. It doesn't help in my case anyway. Any ideas?

---

