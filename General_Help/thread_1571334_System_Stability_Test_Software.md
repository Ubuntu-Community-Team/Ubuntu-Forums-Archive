---
title: "System Stability Test Software"
date: 2010-09-09
forum: General Help
---

### Post by waspinator on 2010-09-09
Hi,

I'm looking for system stability test software to stress test all of my hardware. I used to use Everest on windows, and I found a closed source program called burnintest that should do what I like, but it uses KDE 3, which I never use. Is there a ubuntu friendly (open source a plus) stability software in existence?

If nothing exists, I'll have to make one.

Thanks,

Waspinator



Linux/KDE (closed): [http://www.passmark.com/products/bitlinux.htm](http://www.passmark.com/products/bitlinux.htm)
Linux (open, limited options): [http://systester.sourceforge.net/about.html](http://systester.sourceforge.net/about.html)

Windows: [http://www.lavalys.com/products](http://www.lavalys.com/products)

---

### Post by MountainX on 2010-10-27
See if this helps:
[http://manpages.ubuntu.com/manpages/hardy/man1/stress.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/stress.1.html)

```
$ sudo apt-get install stress
$ stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 10s
```

[http://packages.ubuntu.com/search?keywords=stress](http://packages.ubuntu.com/search?keywords=stress)

---

### Post by MountainX on 2010-10-27
Also, check out these threads:
[http://ubuntuforums.org/showthread.php?t=1400815](http://ubuntuforums.org/showthread.php?t=1400815)
[http://ubuntuforums.org/showthread.php?t=869780](http://ubuntuforums.org/showthread.php?t=869780)
[http://www.overclockers.com/forums/showthread.php?t=486495](http://www.overclockers.com/forums/showthread.php?t=486495)

---

