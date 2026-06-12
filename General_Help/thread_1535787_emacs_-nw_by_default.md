---
title: "emacs -nw by default"
date: 2010-07-21
forum: General Help
---

### Post by bonfire89 on 2010-07-21
Hi there,

I'm looking to have emacs always open in the terminal. Is there anyway that I can do this?

Is there a way that a switch can be included with a command by default?


Thanks.

---

### Post by Zorgoth on 2010-07-21
You could create something in your $PATH that just runs emacs -nw/edit the launchers.

---

### Post by baltazar3 on 2010-07-21
alias emacs='emacs -nw'
put in .bashrc to always have it that way.

---

### Post by RiceMonster on 2010-07-21
edit ~/.bashrc and add this line:
```
alias emacs='emacs -nw'
```

---

### Post by bonfire89 on 2010-07-21
beautiful!


Thanks all!




I was thinking in the area of an alias, but I wasn't sure how it would handle other switches and such, but it seems that the alias simply expands and thus whatever I type after emacs is appended to the expansion of the alias. Very cool. This will be useful in the future.

---

### Post by Zorgoth on 2010-07-21
To do that from a launcher just edit the launcher to be an "application in terminal" rather than an "application."

---

