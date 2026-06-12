---
title: "nosey co-worker"
date: 2010-02-10
forum: General Help
---

### Post by denti on 2010-02-10
hi, i've got a nosey co-worker that keeps looking at my screen and commenting on what i'm working on.
told them to stop several times to no avail. 
is there a program that i can turn the screen off in a keystroke or have screen saver turn on in a keystroke?

---

### Post by snowpine on 2010-02-10
If you were doing your work instead of surfing UbuntuForums, you would have nothing to hide. ;)

---

### Post by patchwork on 2010-02-10
CTRL-ALT-F1 will drop you to console, and CTRL-ALT-F7 will return you to X

---

### Post by snowpine on 2010-02-10
Ctrl+Alt+left/right arrow will move you to a different desktop.

---

### Post by denti on 2010-02-10
ahh perfect. thank you.
btw, i am doing my work but not a fan of ppl commenting on what i'm working on nor reading my email and commenting on that too :)

---

### Post by amac777 on 2010-02-10
Ctrl+Alt+L will turn your screen saver on (and lock the screen).

---

### Post by Rhubarb on 2010-02-10
Try **cappuccino** from the ubuntu repositories
*an utility to let your boss think that you're working hard*

While it's not really the best solution for you, it's not bad either.

You could always bind a key combo to load up a picture / document fullscreen that bluntly states "stop being nosey, it's annoying"

Another app you could bind to is a simple bash script that uses **sm**
```
#!/bin/bash
sm "stop being nosey, it's annoying"
exit 0
```
(sm) is another good app for making full-screen text on your monitor that's really very visible.
Press "ctrl + q" to quit sm

---

