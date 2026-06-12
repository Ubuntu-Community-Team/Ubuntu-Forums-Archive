---
title: "Zsh history"
date: 2010-03-05
forum: General Help
---

### Post by Intrepid Ibex on 2010-03-05
When pressing up key, I get the same commands as many times as I executed them in zsh.

How to have the same one only once?

---

### Post by ibuclaw on 2010-03-05
In Zsh, you would put in your config file
```
setopt hist_ignore_dups
```

See here for more history options: [http://unix.derkeiler.com/Newsgroups/comp.unix.shell/2004-05/1063.html](http://unix.derkeiler.com/Newsgroups/comp.unix.shell/2004-05/1063.html)

(edit):
And if anyone else is interested, the following in bashrc:
```
export HISTCONTROL=erasedups
```
Will invoke a similar behaviour.

Regards
Iain

---

### Post by Intrepid Ibex on 2010-03-05
Niiiiiiicccccceeeeeee....

---

