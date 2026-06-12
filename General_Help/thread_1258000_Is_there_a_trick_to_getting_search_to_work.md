---
title: "Is there a trick to getting search to work?"
date: 2009-09-04
forum: General Help
---

### Post by morganpatrick on 2009-09-04
I'm trying to search for a file in my filesystem and Ubuntu search just won't find it. I'll search from Places, select "Show hidden and backup files" and then I'll navigate to a folder like .config/autostart, make sure it's there, then search for "autostart" and it turns up nothing.

What am I missing here?

edit: You know what I was missing? Hitting the 'add' button. I'm a dummy!

---

### Post by jonobr on 2009-09-04
maybe try finding in the terminal.

So if your looking for foo.txt that is somewhere in the Desktop menu or below

You could

```
find ~/Desktop -name foo.txt
```

You could wildcard

```
find ~/Desktop -name foo.*
```
or 
```
find ~/Desktop -name *.txt
```

Or if you know its somewhere in you home directory

```
find . -name  foo.txt
```

Case sensitivity is important here.

If that works and the other doesnt, maybe you found yourself an interesting problem.

---

