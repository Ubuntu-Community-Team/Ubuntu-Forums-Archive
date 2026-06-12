---
title: "pipe grep and less"
date: 2010-09-01
forum: General Help
---

### Post by l3ecl on 2010-09-01
So theres this command 
```
man -k mail 
```Which lists commands that contain the keyword "mail" in their description.
 I want the output of this command in less and the words highlighted by grep. Something like 

```
man -k mail | grep mail | less
```The command doesn't work, how do I fix it?

---

### Post by spjackson on 2010-09-01
> **l3ecl said:**
> I want the output of this command in less and the words highlighted by grep.
How about this?
```
man -k mail | grep --color=always -i mail | less --raw-control-chars
```

---

### Post by l3ecl on 2010-09-01
that's really awesome! how did you learn how to do that?

and howcome if i type 

```
man -k mail | grep mail | less
```

it doesn't work?

---

