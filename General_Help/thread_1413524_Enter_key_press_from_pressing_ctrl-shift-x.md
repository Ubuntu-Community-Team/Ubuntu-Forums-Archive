---
title: "Enter key press from pressing ctrl-shift-x"
date: 2010-02-22
forum: General Help
---

### Post by Intrepid Ibex on 2010-02-22
Anybody know how to have Enter key pressed from pressing Ctrl-Shift-X?

I need it with Zsh + Konsole + 'Clear & Reset' (Konsole feature).

---

### Post by tom4everitt on 2010-02-22
What you want to look into is probably xmodmap. You can probably find something on google on how to the exact syntax of such a config file should work. 

A very useful command when dealing with this kind of stuff is xev, which tells you exactly what key events that occur.

---

### Post by Intrepid Ibex on 2010-02-22
Friggin' fast response.

But I'm already using xbindkeys - wouldn't wanna have them both.

---

### Post by Intrepid Ibex on 2010-02-23
Aaaanyone?

---

### Post by tom4everitt on 2010-02-23
But you have to use something like xmodmap or xbindkeys. So either mix them or do everything in one of them. Then you can narrow down your question to a pure syntax question of either (which you might even solve by just googling...). I'm sorry I don't have any more specific info to give you, maybe someone else do?

---

### Post by Intrepid Ibex on 2010-02-24
The problem with xbindkeys is indeed that I dunno how to have multiple key strokes in xbindkeys and that what's the command to just press enter.  I could also just set it in .zshrc but I dunno how to do that either... well googling didn't find much anyways..

If someone has the answer I'd be happy to hear it.

---

### Post by Intrepid Ibex on 2010-03-03
bumputi bump

---

### Post by Intrepid Ibex on 2010-03-24
Okay, well got to the part where I need to find out the command for executing "enter".

---

### Post by Intrepid Ibex on 2010-04-03
Bump. No one knows what is the command for "enter"?

---

### Post by Intrepid Ibex on 2010-04-11
Xvkbd... solved.

---

