---
title: "Conky on startup"
date: 2009-10-24
forum: General Help
---

### Post by m0sh on 2009-10-24
Im not 100% sure if this is the right place to post this thread so if it needs to get moved please do.  Anyway... I have managed to get Conky somewhat working on my fresh Ubuntu system but I'd like it to run on startup.  How can I do this?  Any help would be highly apprecaited.
Thanks guys-
Doug

---

### Post by Yvan300 on 2009-10-24
Go into Startup applications and add one with the command conky and you'r done.

---

### Post by falconindy on 2009-10-24
Depending on your window manager (particularly Compiz) and the way you've setup Conky, you may need to delay the start of Conky to ensure that its window is created by the window manager of your choosing. To do so, make a script:
```
#!/bin/sh
sleep 20
conky &
```
Call it something like startconky.sh. Move it into $HOME/bin (you may need to create bin), and then execute `chmod +x startconky.sh`. Add that to your startup programs as '/home/<username>/bin/startconky.sh'.

---

