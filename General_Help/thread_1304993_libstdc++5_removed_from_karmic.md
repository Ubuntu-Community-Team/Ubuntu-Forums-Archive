---
title: "libstdc++5 removed from karmic?"
date: 2009-10-29
forum: General Help
---

### Post by tuxx on 2009-10-29
Hello,

I use a program (Bibble Labs Pro 4) which depend on libstdc++5 (not possible with v.6 nor a symlink to trick it to use it).

Worked perfectly within 9.04 and prior.

Now with Karmic I'm unable to install from apt and manually my program fails also.

So.. should I put my money on getting libstdc++5 back in repo or look elsewhere?

Thanks in advance!

---

### Post by lykwydchykyn on 2009-10-29
I downloaded the .deb from Jaunty and installed it manually, seemed to do the trick for me (I needed it for GroupWise).

Get it here:

[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

---

### Post by tuxx on 2009-10-30
Shoot I forgot to mention that, sorry, but I already tried that and made the appropriate symlinks in /var/lib32 (it's a 32 bit program).

---

### Post by tuxx on 2009-10-30
Hello again!

well well, I tried to reinstall it and remake the symlinks - now it works. Something must have been messed up yesterday as I tried it.

Thanks!

---

