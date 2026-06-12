---
title: "make command to run only with specific parameters"
date: 2012-04-06
forum: General Help
---

### Post by tripialos on 2012-04-06
Hi ...again

Is it possible to force a command to be run only with specific parameters?

For instance i would like the command iptables to be run only with paramter lets say -L

thanks

---

### Post by spillin_dylan on 2012-04-06
Not exactly sure if this is exactly what you want, but you can make an alias.

```
alias iptables='iptables -L'
alias ls='ls --color=auto --classify --human-readable --group-directories-first
```

You can type them in at any command line prompt, or better yet, add them to ~/.bash_aliases to make them apply every time you log in.

---

### Post by tripialos on 2012-04-07
> **spillin_dylan said:**
> Not exactly sure if this is exactly what you want, but you can make an alias.

```
alias iptables='iptables -L'
alias ls='ls --color=auto --classify --human-readable --group-directories-first
```

You can type them in at any command line prompt, or better yet, add them to ~/.bash_aliases to make them apply every time you log in.

Wicked! Thanks spillin!

---

