---
title: "kate causes 12.04 to crash."
date: 2012-07-03
forum: General Help
---

### Post by davemar on 2012-07-03
I'm running 12.04 with the gnome desktop on a 64-bit machine. I tried starting up 'kate' (the text editor), but it crashes as soon as the file I'm viewing appears. When I say crash, it actually goes for a reboot, so I can't read any of kate's messages whizzing past in the terminal window for any clues.

Anyone has experience of this?

---

### Post by cipherboy_loc on 2012-07-03
Try running Kate from the terminal again, except redirect the output to a file:

```

kate > ~/errors

```


Cipherboy

---

### Post by davemar on 2012-07-03
I did it this way as the output is to stderr of course:
```
kate >& ~/errors
```
Anyway here are the last 4 lines of that which appear to be the important ones:
```

kate: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.0.
kdeinit4: Fatal IO error: client killed
klauncher: Exiting on signal 15
kdeinit4: kded4 [kdeinit]: Fatal IO error 11 (Resource temporarily unavailable) on X server :2.0.

```

---

