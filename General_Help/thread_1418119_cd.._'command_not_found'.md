---
title: "cd.. 'command not found'"
date: 2010-02-28
forum: General Help
---

### Post by ricardino on 2010-02-28
Hi all, ive got a bit of a strange problem with terminal. Ive just installed ubuntu 9.10, however terminal doesnt seem to recognising the 'cd..' command. I can cd forward in a directory ok, but i cant go backwards. Whenever i try to use 'cd..' or 'cd.' i get the error: 'cd..: Command not found'. I thought it was a bit odd, because surely the cd command is a core terminal function?

Any help would be appreciated. Thanks.

---

### Post by stoneage on 2010-02-28
To go back one directory use ```
cd ../
```

---

### Post by 3rdalbum on 2010-02-28
There is no "cd.." or "cd." command; only the "cd" command.

Looks like you're missing a space - it should be:

```
cd ../
```

---

