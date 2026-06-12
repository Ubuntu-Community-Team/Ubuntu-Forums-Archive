---
title: "Send command from tty to X?"
date: 2012-01-31
forum: General Help
---

### Post by Intrepid Ibex on 2012-01-31
Hey,

What's the simplest way to send a command to another tty?

E.g. if I wanted to run 'xmonad --replace' in X but was unable to do so, how could I send the command from another tty to there?

---

### Post by Intrepid Ibex on 2012-04-15
lolololo

---

### Post by mhgsys on 2012-04-15
[http://www.manpagez.com/man/1/screen/](http://www.manpagez.com/man/1/screen/)

although for launching X programs from a tty outside X one should use export DISPLAY=:0 before program launch

---

### Post by BrnKthSrnsn on 2012-06-03
Try 'writevt'.  [http://www.linuxquestions.org/questions/linux-software-2/send-a-command-to-a-another-tty-495598/](http://www.linuxquestions.org/questions/linux-software-2/send-a-command-to-a-another-tty-495598/)

---

