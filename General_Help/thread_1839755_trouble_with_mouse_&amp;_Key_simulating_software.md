---
title: "trouble with mouse &amp; Key simulating software"
date: 2011-09-06
forum: General Help
---

### Post by Arminius on 2011-09-06
I've tried the program Xnee, but it keeps crashing whenever I try to lauch the GUI, and the command line doesn't record any mouse movements.

So does anyone know any other software that will just execute specific mouse movements, mouse clicks, and send key functions?

---

### Post by stinkeye on 2011-09-06
xdotool.
It's in the repos.
```
sudo apt-get install xdotool
```
For info after install enter in the terminal
```
man xdotool
```

Depending on what your doing you might also find 
**easystroke** useful.
A mouse gestures application.

---

### Post by PGScooter on 2012-01-24
> **Arminius said:**
> I've tried the program Xnee, but it keeps crashing whenever I try to lauch the GUI, and the command line doesn't record any mouse movements.

So does anyone know any other software that will just execute specific mouse movements, mouse clicks, and send key functions?

Arminius,

Xnee 3.11 was just released last month. I'd be curious to know if it solved your problem.
announcement:
[http://sandklef.wordpress.com/2011/12/16/gnu-xnee-3-11-jansch-released/](http://sandklef.wordpress.com/2011/12/16/gnu-xnee-3-11-jansch-released/)
downlaod:
[http://ftp.gnu.org/gnu/xnee/](http://ftp.gnu.org/gnu/xnee/)

---

