---
title: "Misaligned TTY's"
date: 2010-05-08
forum: General Help
---

### Post by thatsPipe on 2010-05-08
I'm running 10.04 with the NVidia drivers from the repos and after my latest reset, I found that all my tty screens (the ones accessible by ctrl+alt+F*) are misaligned to the point of being absolutely useless.

By misaligned, I mean that only the bottom 1/10th of the screen is used and the entire thing is shifted to the right of the monitor so that all I see when switching to a tty is 'Ubuntu 10.04 LTS rshaw-desktop tty1'.

Typing still works as I can login and then type enough crap to cause the text to start scrolling but only that bottom 1/10th of the screen is all that is used.

---

### Post by thatsPipe on 2010-05-10
Bump. Anyone have any idea? Anything?

---

### Post by obaid on 2010-05-10
your screen is LCD or CRT ?

---

### Post by thatsPipe on 2010-05-10
LCD over a DVI connection.

---

### Post by junapp on 2010-05-10
just a shot in the dark, but do you have an auto-adjust feature on your monitor? If so, try it.

If you are pretty sure it has nothing to do with the monitor a second guess would be to run
sudo dpkg-reconfigure console-setup

but if you can't see the options, that may not be a good choice. This guy had some problems:
[http://ubuntuforums.org/showthread.php?t=598969](http://ubuntuforums.org/showthread.php?t=598969)

---

