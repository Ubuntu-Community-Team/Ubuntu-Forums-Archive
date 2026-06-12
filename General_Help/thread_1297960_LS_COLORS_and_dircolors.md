---
title: "LS_COLORS and dircolors"
date: 2009-10-22
forum: General Help
---

### Post by hwttdz on 2009-10-22
What file does dircolors read or what file is used to set the default LS_COLORS value?  I don't see it in the manual of either ls or dircolors. 

Also what is priority order when determining color?  i.e. if there is a global write mp3 file that's colored as a global write file and not as an mp3 file.  

Thanks.

---

### Post by alphaniner on 2009-10-22
From the man page:

> If  FILE  is  specified, read it to determine which colors to use for which file types and extensions. **Otherwise, a precompiled database is used.**

IOW, maybe it's not from a file.

---

### Post by Giblet5 on 2009-10-22
I think vanilla Ubuntu uses builtin defaults.

You can create a file to be edited using ```
dircolors --print > .mydircolors
```

Edit that as you see fit.

Then you can add a line to read that during the login phase by adding ```
...

if [ -f "$HOME/.mydircolors" ] ; then
  export LS_COLORS=`dircolors -b "$HOME/.mydircolors"`
fi

...
``` to your ~/.bashrc

---

### Post by hwttdz on 2009-12-11
If one is using bash one can do 

```
dircolors -b > ~/.dircolors
```

then add

```
if [ -f ~/.dircolors ]; then
    . ~/.dircolors
fi
```

to the .bashrc (you can adjust these commands for other shells).

---

