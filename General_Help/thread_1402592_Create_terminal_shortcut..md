---
title: "Create terminal shortcut."
date: 2010-02-09
forum: General Help
---

### Post by HomoGleek on 2010-02-09
There are commands I use alot in the terminal that change a little each time.

Example 
```
get_iplayer field=name WHAT-IM-SEARCHING-FOR
```

but I want to be able to type
```

gi WHAT-IM-SEARCHING-FOR
```

Possible?

---

### Post by DaithiF on 2010-02-09
add this to your .bashrc file:

```
function gi () 
{
  get_iplayer field=name $@
}
```

---

### Post by shriramrs31 on 2010-02-09
you can also use the shell "alias" command

---

### Post by HomoGleek on 2010-02-09
> **DaithiF said:**
> add this to your .bashrc file:

```
function gi () 
{
  get_iplayer field=name $@
}
```
Thanks, that worked. 

Any ideas why this one wont work?

```
function iplay () 
{

get_iplayer --stream $@   --player="mplayer -cache 3072 -"

}
```

---

### Post by DaithiF on 2010-02-09
sorry, no.  i don't know what iplayer is.  Maybe try enclosing the $@ in quotes.

---

