---
title: "Ubuntu 9.10 amd64 recursive grep problem"
date: 2010-01-01
forum: General Help
---

### Post by Nick Payne on 2010-01-01
Ubuntu 9.10 amd64. I'm trying to find all files of a certain type in a directory structure that contain a particular text string. According to my reading of 'grep --help' and 'man grep', the following should work, but it only finds matching files in the current directory:

```
grep -rn '\\slide' *.ly
```

what does work is

```
find -name '*.ly' | xargs grep -n '\\slide'
```

Why doesn't grep -r on its own recurse through the directory structure?

---

### Post by DaithiF on 2010-01-02
because you're limiting grep to only looking at '*.ly' files, and so it won't look at any directories (unless they happened to be named *.ly of course).  If it doesn't look at directories then its not going to recurse into them.

You can change things like so to do what you want:
```
grep -rn --include='*.ly' searchterm *
```

---

