---
title: "How to traverse a directory with certain permissions?"
date: 2011-06-30
forum: General Help
---

### Post by Externalist on 2011-06-30
Hi,

I'm trying to create a script that when given a directory, it goes traverses through all the subdirectories and process the files in them.
However, there is one restriction. The directories that it traverses through must all have a read permission for the others group.
How would I go about doing this?

Thanks! :)

---

### Post by sisco311 on 2011-06-30
Do you want to do it recursively? Could you please post an example of the directory structure?

---

### Post by arius13721 on 2011-06-30
I think you may be looking for something like this:

```
find ./ -type d -group others -perm /g+r
```

**-type d**: Lists only directories, not files
**-group others**: List those that have the group set to others
**-perm /g+r**: And the group read-bit is set.

Hope that helps.

---

