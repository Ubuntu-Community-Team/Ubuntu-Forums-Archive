---
title: "Where to find kile-dbg package?"
date: 2009-11-29
forum: General Help
---

### Post by P3t3r on 2009-11-29
I have a crash report from Kile, and I want to send debug information. However, next to the general packages kdelibs5-dbg and kdepim-dbg it seems I need a specific package kile-dbg.

However, sudo apt-get install kile-dbg can't find anything. I wonder how and where to find this package, as google seems incapable of telling me. Thanks!

---

### Post by P3t3r on 2009-12-08
Anyone? I'm clueless where to search for this package. :(

---

### Post by Zorael on 2009-12-08
Indeed, it doesn't seem to be in the repos.

I'd try #kubuntu-devel or #ubuntu-motu on irc.freenode.net.

---

### Post by P3t3r on 2009-12-13
I don't understand, how can I install a package over IRC?

---

### Post by Zorael on 2009-12-13
Ah, no; I mean you could try asking the Kubuntu developers over there. Perhaps there's been a packaging error, or perhaps its debugging symbols are in a different package by design.

---

### Post by laverde on 2010-07-18
I guess it is not useful for you any more, but it could help somebody else.

I have had the same problem, the progress report creator couldn't find katepart.so and it was in kdelib5-dbg 

Other libs I had to install were

kdelibs-dbg
libqt4-dbg
libglib2.0-0-dbg

but looking for them was straightforward 

I think required libs change according to the crash

It looks like there are no dbg specific to kile to be installed.

---

