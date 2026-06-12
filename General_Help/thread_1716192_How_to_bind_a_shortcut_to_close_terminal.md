---
title: "How to bind a shortcut to close terminal?"
date: 2011-03-28
forum: General Help
---

### Post by kmcbest on 2011-03-28
Hi, I want to bind a key to close terminal window in my ~/.inputrc

I've successfully bind "double Esc" to clear a line like this
```
"\e\e": kill-whole-line
```but I didn't find the command for close/exit/quit a terminal window.

Please help, thanks.

---

### Post by nothingspecial on 2011-03-28
```
exit
```

---

### Post by kmcbest on 2011-03-28
Thx but I've tried, it doesn't work, I've put this into inputrc:

```
"\c-w": exit
```then save, open a new terminal, press "ctrl+w", but the terminal is not closed.

---

### Post by nothingspecial on 2011-03-28
That is probably because your .inputrc is for bash shortcuts, not window management. I'm not sure how you would close a specific window.

In your keyboard shortcuts you could put ```
killall gnome-terminal
``` or killall terminator or whatever you use but that would kill all of them.

There may be a way with compiz window rules or  something, sorry not sure.

---

### Post by deconstrained on 2011-03-28
Ctrl-D

---

### Post by kmcbest on 2011-03-28
> **deconstrained said:**
> Ctrl-D
That works. I think I can stick to this shortcut as it's as simple as ctrl+w. 

A side note: when I press ctrl+D I see the "exit" text entered, so maybe this ctrl+D shortcut is defined elsewhere?

Well there's even another way I've digged: in gconf-editor -> app -> gnome-terminal -> keybindings, you can change the default keys :D

Thanks both for the head-up's, solved.

---

### Post by fabricator4 on 2011-03-28
> **kmcbest said:**
> Hi, I want to bind a key to close terminal window in my ~/.inputrc

I've successfully bind "double Esc" to clear a line like this
```
"\e\e": kill-whole-line
```
but I didn't find the command for close/exit/quit a terminal window.

Please help, thanks.


Thanks, I'm learning by reading.  I've wanted that kill whole line functionality for a while now.

In searching for the "exit" command to do this, I found out that there's already a key binding defined that works fine: <ctrl>d

What I _didn't_ find was a list of possible commands that will work with key bindings.  Odd, I must be using the wrong search terms.

Chris.

---

### Post by deconstrained on 2011-03-28
> **kmcbest said:**
> A side note: when I press ctrl+D I see the "exit" text entered, so maybe this ctrl+D shortcut is defined elsewhere?
^D is a bash metachar for exit (it works on tty's and when ssh'd!). Whether "exit" is actually printed out depends on an environment variable I think, but I'm not sure. But ^D is intrinsic to bash and isn't to my knowledge changeable.

---

