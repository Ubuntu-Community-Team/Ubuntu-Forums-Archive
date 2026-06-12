---
title: "Can't spawn xvfb from command-line app"
date: 2010-05-18
forum: General Help
---

### Post by Matthew Gertner on 2010-05-18
I've written a command-line application in C which spawns Firefox using the system() function. This works fine on a system with a display, but I also need to run it on headless computers running Linux. To do so, I tried to spawn Firefox in the same way (i.e. by passing the command line to the system() function) but using xvfb (i.e. something like "xvfb-run firefox"). This fails with the following error (on both Debian and Ubuntu):

Xvfb failed to start

Presumably xvfb doesn't like the way I'm forking my console process using the system() API. Is there a better way for my C app to spawn xvfb?

Apologies if this isn't the right place to ask this. If that's the case, can someone point me to a better forum for this type of question?

Thanks,
Matt

---

