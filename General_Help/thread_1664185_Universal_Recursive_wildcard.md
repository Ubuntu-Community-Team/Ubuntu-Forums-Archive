---
title: "Universal Recursive wildcard"
date: 2011-01-10
forum: General Help
---

### Post by tjfitz on 2011-01-10
I remember seeing a bash string that was, effectively, a wildcard for every file and directory at the current level (including hidden files).  I think there was a ** and a // and of course a *.* in there somewhere....  Anyone care to unveil the mystery?

---

### Post by sisco311 on 2011-01-10
If the dotglob option is enabled, then * matches any file exept the hard 
links to the current and parent directories (. and ..):

```
shopt -s dotglob
echo *
shopt -u dotglob
```

---

### Post by tjfitz on 2011-01-14
I failed to mention (but included it in the thread title) that it did this *recursively*.  I don't think it needed any special options enabled.

---

### Post by sisco311 on 2011-01-14
As far as I know, in bash, you have to enable both globstar and dotglob to be able to match any file recursively with a single pattern:
```
shopt -s globstar dotglob
echo **/*
```

See:
```
man bash | less +2/"Pathname Expansion"
```
```
man bash | less +2/"Pattern Matching"
```
and
[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)

I don't know much about other shells, but in zsh:
```
echo **/{.,}*
```
seams to work with the default/recommended settings.

---

### Post by tjfitz on 2011-01-15
Ok, perhaps I was seeing this done in another shell.  Thanks!

---

