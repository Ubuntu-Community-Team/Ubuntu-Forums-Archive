---
title: "GCC environment variables"
date: 2011-02-26
forum: General Help
---

### Post by Beowolf64 on 2011-02-26
What is the best way to set them permanently? Different sources give different  recipes. 
I put this at the end of ~/.bashrc file, but not sure if it is the best solution.

```
CPATH=/media/docs/cpp/include
export CPATH

C_INCLUDE_PATH=/media/docs/cpp/include
export C_INCLUDE_PATH

CPLUS_INCLUDE_PATH=/media/docs/cpp/include
export CPLUS_INCLUDE_PATH

LIBRARY_PATH=$HOME/lib
export LIBRARY_PATH

LD_LIBRARY_PATH=$HOME/lib
export LD_LIBRARY_PATH
```

---

### Post by down_to_earth_sort_of_guy on 2011-02-26
I have bash scripts like :

~/bin/environments/gcc

and an alias in .bashrc which says:

alias +gcc='. ~/bin/environments/gcc'

(notice the DOT and SPACE before ~)

So this does not polute the environment when using different platforms.

if I want to work with gcc I just type +gcc at the prompt.

Also, this allows for configuring scripts to use multiple environments.

btw, using something like autoconf/automake might be better for you if you are using this for a specific project only.

---

