---
title: "Ubuntu Crash?"
date: 2010-02-16
forum: General Help
---

### Post by ComptutsXV on 2010-02-16
When I loaded up a game called Alien Arena, I tried to play it but my screen goes black and has a bunch of green text. But im able to type stuff in but everytime I click enter it says invalid command. I have to turn my computer off and back on and everything is fine. Is this a crash? I dont think its my graphics card, but in case your wondering my graphics card is a Nvida GeForce 9500 GT.

---

### Post by ComptutsXV on 2010-02-16
Bump

---

### Post by ComptutsXV on 2010-02-16
Can anyone help?

---

### Post by ironclaw on 2010-02-17
When that happens, try switching to a virtual terminal by pressing <Ctrl><Alt><F1>. Log in and run 'top' to see which processes are taking up CPU cycles (press 'Q' to exit top). You can also run
```
killall alien-arena
```
to send a termination signal to 'alien-arena'.

Press <Ctrl><Alt><F7> to switch back to the X display (i.e., the normal graphical display).

---

### Post by ComptutsXV on 2010-02-20
Ok thanks a lot!

---

