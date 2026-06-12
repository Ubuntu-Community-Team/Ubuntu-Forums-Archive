---
title: "BASH: cycle through last arguments in vi mode?"
date: 2009-12-11
forum: General Help
---

### Post by Stefanie on 2009-12-11
In the default editing mode for bash (emacs), you can press alt-. to cycle through the last arguments of previous commands. When you use vi mode, however (set -o vi), this doesn't work anymore. Does anyone know the vi shortcut for alt-.?

---

### Post by john newbuntu on 2009-12-11
Try Esc and then "k" (without quotes)

---

### Post by Stefanie on 2009-12-11
I'm sorry but that's not what I mean. k and j just cycle through the command line history and not through the history of the last arguments you used.

---

### Post by ttsiodras on 2012-03-19
> **Stefanie said:**
> In the default editing mode for bash (emacs), you can press alt-. to cycle through the last arguments of previous commands. When you use vi mode, however (set -o vi), this doesn't work anymore. Does anyone know the vi shortcut for alt-.?

Sure - just use this in your .bashrc:

```

set -o vi
bind -m vi-command ".":insert-last-argument
bind -m vi-insert "\C-l.":clear-screen
bind -m vi-insert "\C-a.":beginning-of-line
bind -m vi-insert "\C-e.":end-of-line
bind -m vi-insert "\C-w.":backward-kill-word

```

This way, not only ESC-dot but also Ctrl-A, Ctrl-E, Ctrl-W and Ctrl-L will work as you expect. You can still switch to vi command mode (with ESC) and enjoy the immense powers of vi, so you have the best of both worlds.

---

