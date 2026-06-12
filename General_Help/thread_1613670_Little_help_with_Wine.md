---
title: "Little help with Wine?"
date: 2010-11-04
forum: General Help
---

### Post by x Da B0mB on 2010-11-04
Ok so, I had Wine working for a little bit, but one day when i went to launch a program i got this error:

No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

Any suggestions? I am running 32bit Kubuntu 10.10.

Thanks!!:D

---

### Post by 3Miro on 2010-11-04
1. Is everything else working fine (i.e. can like the other graphics in Kubuntu).

2. Are you running wine as a different user (as for example sudo wine, which you should never do).

3. What happens if you type:
```
 $DISPLAY 
```
in the terminal.

If graphics is working and you get nothing back from DISPLAY, then you can try:
```
 export DISPLAY=":0.0" 
```
and then run your program from the same terminal. Let me know if this works.

---

