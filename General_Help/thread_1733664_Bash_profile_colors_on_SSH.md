---
title: "Bash profile colors on SSH"
date: 2011-04-19
forum: General Help
---

### Post by hojjat on 2011-04-19
I have modified my .bashrc to make ls color file like this:

```
alias ls='ls --color=auto'
```

However, it doesn't work when I log on to the machine on SSH. It works if I call "ls --color=auto", but ls alone is still colorless. What am I missing?

---

### Post by ~Plue on 2011-04-19
you'll need to source your .bashrc in .bash_profile (create it if you dont have one)
in it, enter;
```

[[ -f ~/.bashrc ]] && . ~/.bashrc
```

---

### Post by emrys.r on 2013-01-25
Perfect, Thanks!

---

