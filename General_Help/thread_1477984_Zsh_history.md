---
title: "Zsh history"
date: 2010-05-09
forum: General Help
---

### Post by Intrepid Ibex on 2010-05-09
How can I preserve the command history in/for Zsh after boot?

---

### Post by louieb on 2010-05-09
Command history is defined in .zshrc   - not a zsh expert but I do use it for my login shell.

Found this .zshrc file on the net a few years back  - been using it ever since - history and auto completion are built-in  

[http://paste.ubuntu.com/430571/](http://paste.ubuntu.com/430571/)

---

### Post by Intrepid Ibex on 2010-05-09
Thanks, doggie =). It was this part (the history needs to be saved to a file (*.bash_history* with bash). Otherwise it's gonna float in your RAM at least until you boot):
```
HISTFILE=$HOME/.zhistory # where the file will be saved
HISTSIZE=1000 # the size in bytes it can grow up to
SAVEHIST=1000 # thr maximum number of commands to save I guess
```

---

