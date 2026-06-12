---
title: "Ignore unmet dependencies?"
date: 2009-10-15
forum: General Help
---

### Post by ownaginatious on 2009-10-15
Hey guys,

I'm actually using Debian, but my problem is pretty much the same as it would be in Ubuntu. Anyway, I recently installed the g15daemon package for my keyboard that comes with Debian Lenny, and it contains a subpackage (libg15daemon-client1) that is kind of screwed up (causes the buttons on the keyboard display to randomly press themselves).

Anyway, I've remedied the problem by installing a different subpackage, but now the package manager is complaining because I'm not using the version that came with g15daemon.

So my question is, is there a way to have the package manager just ignore this? I know for a fact that there is nothing wrong with using a different subpackage here (probably whoever compiled it originally accidentally put = rather than >= for acceptable versions).

Thanks!

Dillon

---

### Post by cwbar_1 on 2009-10-15
Somewhere in the package manager, there is a command to "force" version.  I'm not sure where it is, but it is there.

---

