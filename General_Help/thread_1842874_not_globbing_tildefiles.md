---
title: "not globbing tildefiles"
date: 2011-09-12
forum: General Help
---

### Post by hwttdz on 2011-09-12
I have --ignore-backups aliased for ls, but if I were to do "ls *" in a directory it shows me all files ending in tilde.  Can I change the meaning of * to exclude files ending in tilde?

---

### Post by SecretCode on 2011-09-12
Hmm. Looks like you can't, at least not with ls itself - some versions of the man page say
```
`-B'
`--ignore-backups'
    Do not list files that end with `~', unless they are given on the command line.
```
And the shell expansion of '*' means they are given on the command line. 

I'm not aware of any way to change the shell globbing rules themselves (in bash ... you could write your own shell ...)

---

### Post by sisco311 on 2011-09-12
You can't change the meaning of * to exclude ~, but you could use:
```
ls *[^~]
```

---

### Post by hwttdz on 2011-09-12
Actually if you dig deep enough in the bash man pages you will find the GLOBIGNORE variable, and setting it to:

export GLOBIGNORE=".:.*:..:*~"

will ignore "." and ".." (self and up directory), as well as ".gnome2" and ".gnome2forthursday" and all those other config files, and ... drumroll please ... "filename.txt~".  Of course on the downside: there's a distinct possibility of either being captured by the queen of hearts or eaten by the jabberwocky.

---

### Post by sisco311 on 2011-09-12
LOL

I completely forgot about the GLOBIGNORE variable. Nice to see someone how reads the man pages. :)

---

