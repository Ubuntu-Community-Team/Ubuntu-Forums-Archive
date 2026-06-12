---
title: "hard link to folder?"
date: 2009-09-05
forum: General Help
---

### Post by blur xc on 2009-09-05
Can you make a hard link to a folder?

I have a shared music folder- ```
/home/shared/Music
``` and what I would like is to have it linked to my ```
~/Music
``` path so I could type cd Music when I open a terminal rather than ```
cd ../shared/Music
``` or ```
cd /home/shared/Music
``` etc...

I tried```
 cp -l Music ~
``` but it gave me this error message```
 cp: omitting directory `Music'
```Thanks,
BM

---

### Post by CatKiller on 2009-09-05
> **blur xc said:**
> Can you make a hard link to a folder?

No.

You can make a symbolic link though.

---

### Post by c0mput3r_n3rD on 2009-09-05
you use the ln (that's a lower calse L, and an 'n').  you would do something like this:
```

ln ~/music/share ~/music/share.ln

```
the .ln extension shows that it's a symbolic link, which actually points to the directories/files inode number.  you can then move that share.ln where ever you want.

---

