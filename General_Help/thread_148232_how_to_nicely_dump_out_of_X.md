---
title: "how to nicely dump out of X"
date: 2006-03-21
forum: General Help
---

### Post by oldmanstan on 2006-03-21
how can i nicely dump out of the x window system while using ubuntu? i can get out of it with ctl-alt-esc (i think that's it) or whatever it is but then it never wants to start back up.

also, when not using the gui can ubuntu be "easily" set up to run with a frame buffer for higher resolution in console mode?

thanks!

---

### Post by seoatway on 2006-03-21
ctrl-alt-backspace dumps you out and then startx or X will start it up again. If you change your runlevel to 3 instead of 5 you will start up with networking but in terminal mode instead of X and then you can start X when you want later

---

### Post by colo on 2006-03-21
Switch to a VT of choice (by pressing Ctrl+Alt+[1-9]), and issue ```
init 3
``` there as root. This will have gdm/kdm/xdm/whatever stopped.

Framebuffer console is controllable via kernel-commandline-parameters, have a look at this: [http://ruslug.rutgers.edu/~mcgrof/HOWTOS/framebuffer/framebuffer.php](http://ruslug.rutgers.edu/~mcgrof/HOWTOS/framebuffer/framebuffer.php) to get more information concerning this issue.

---

### Post by trent dillman on 2006-03-21
try this in a terminal:

```
sudo /etc/init.d/gdm stop
```

then, to start again...

```
sudo /etc/init.d/gdm start
```

This makes Ubuntu happy on reboot/shutdown concerning pids.

---

