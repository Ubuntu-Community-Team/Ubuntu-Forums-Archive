---
title: "correct syntax for regex in shell script"
date: 2010-11-05
forum: General Help
---

### Post by rawlins02 on 2010-11-05
This command works to find files that have been updated in past 90 minutes:

```

find \( ! -regex '.*/\..*' \) -type f -mmin -90

```

What changes need to be made to set this as an alias in, say, .cshrc file?  I'm getting: 

alias: No match 

when sourcing .cshrc after adding this line:

```

alias   'find \( ! -regex '.*/\..*' \) -type f -mmin -90'

```

Also, I'm getting a permission denied on output of these files:
 
find: `./.mozilla/firefox/qsqcohjy.default/minidumps': Permission denied
find: `./.mozilla/firefox/Crash Reports': Permission denied

even though I'm trying to ignore all dot files.

---

### Post by AlphaLexman on 2010-11-05
I don't know csh very well, but I think:
> **rawlins02 said:**
> alias   'find \( ! -regex '.*/\..*' \) -type f -mmin -90'
Should be:
```
alias [COLOR=Red]ninety[/COLOR]  'find \( ! -regex '.*/\..*' \) -type f -mmin -90'
```

---

### Post by DaithiF on 2010-11-05
> **rawlins02 said:**
> Also, I'm getting a permission denied on output of these files:
 
find: `./.mozilla/firefox/qsqcohjy.default/minidumps': Permission denied
find: `./.mozilla/firefox/Crash Reports': Permission denied

even though I'm trying to ignore all dot files.

your regex indeed tells find to ignore dot files / directories, but it doesn't prevent find from descending into .dot directories to find non-dot files / directories in there.  For that you need the -prune command.  Something like:

```
find . -regex '.*/\..*' -prune -o -type f -print 
```

---

### Post by rawlins02 on 2010-11-05
> **AlphaLexman said:**
> I don't know csh very well, but I think:

Should be:
```
alias [COLOR=Red]ninety[/COLOR]  'find \( ! -regex '.*/\..*' \) -type f -mmin -90'
```


Still getting alias: No match

---

### Post by rawlins02 on 2010-11-05
> **DaithiF said:**
> your regex indeed tells find to ignore dot files / directories, but it doesn't prevent find from descending into .dot directories to find non-dot files / directories in there.  For that you need the -prune command.  Something like:

```
find . -regex '.*/\..*' -prune -o -type f -print 
```


I just tried:

```

find \( ! -regex '.*/\..*' \) -type f -mmin -90 -prune -o -type f -print

```

and it listed everything in my home area, as if the -mmin 90 was never executed.

---

### Post by DaithiF on 2010-11-05
> **rawlins02 said:**
> I just tried:

```

find \( ! -regex '.*/\..*' \) -type f -mmin -90 -prune -o -type f -print

```and it listed everything in my home area, as if the -mmin 90 was never executed.

 -prune only applies to directories, you have applied it after a -type f constraint and so it has no effect, and as a result the piece after the -o clause is the only part that has any effect (ie. -type f -print).  So you get every file listed.  I'm not sure you have understood what I was suggesting so I would suggest reading the man page for find.  Or if you just want something that works then try:

```
find -regex '.*/\..*' -prune -o -type f -mmin -90 -print

```

---

