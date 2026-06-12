---
title: "How do I delete everything in a partition, except for one directory?"
date: 2009-10-06
forum: General Help
---

### Post by jon.reeve on 2009-10-06
I want to delete everything in a partition, including hidden files, but leave one directory untouched. Is there a command I can use to do that?

---

### Post by sisco311 on 2009-10-06
**[COLOR="Black"]BE CAREFUL WITH THE COMMAND!!![/COLOR]**

```

cd /path/to/partition
[COLOR="DarkOrange"]rm[/COLOR] [COLOR="Red"]-rf[/COLOR] [COLOR="Blue"].[a-zA-Z0-9]*[/COLOR] [COLOR="SeaGreen"]!(filename)[/COLOR] 

```
[COLOR="DarkOrange"]rm = delete files[/COLOR]

[COLOR="Red"]-rf = remove directories and their contents recursively, ignore nonexistent files, never prompt[/COLOR]

[COLOR="Blue"].[a-zA-Z0-9]* = remove hidden files[/COLOR]

[COLOR="SeaGreen"]!(filename) = rm all (non-hidden) except filename (directories are files too :))[/COLOR]


**[COLOR="Black"]BE CAREFUL WITH THE COMMAND!!![/COLOR]**

test it before you run it:
```
echo rm -rf ...
```

---

