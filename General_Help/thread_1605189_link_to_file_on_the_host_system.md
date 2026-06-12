---
title: "link to file on the host system"
date: 2010-10-25
forum: General Help
---

### Post by abhi555 on 2010-10-25
Dear souls:

I installed 10.10 using wubi (Host system is Win XP). I want to create a symbolic link of a file on the host system (Windows c:\abc.doc file) in my Ubuntu home ~/ directory.

When I type command 

[FONT=Courier New][SIZE=2][COLOR=Blue]ln /host/abc.doc abc.doc[/COLOR][/SIZE][/FONT]

It gives me following error

[FONT=Courier New][SIZE=2][COLOR=Blue]ln: creating hard link `abc.doc' => `/host/abc.doc': Invalid cross-device link[/COLOR][/SIZE][/FONT] [COLOR=Blue]

[/COLOR]Any idea what I might be missing?

Thanks,
Abhijit Jawale
(Pune, India)

---

### Post by dcstar on 2010-10-25
> **abhi555 said:**
> Dear souls:

I installed 10.10 using wubi (Host system is Win XP). I want to create a symbolic link of a file on the host system (Windows c:\abc.doc file) in my Ubuntu home ~/ directory.

When I type command 

[FONT=Courier New][SIZE=2][COLOR=Blue]ln /host/abc.doc abc.doc[/COLOR][/SIZE][/FONT]

It gives me following error

[FONT=Courier New][SIZE=2][COLOR=Blue]ln: creating hard link `abc.doc' => `/host/abc.doc': **Invalid cross-device link**[/COLOR][/SIZE][/FONT] [COLOR=Blue]

[/COLOR]Any idea what I might be missing?



You **cannot** have hard links across filesystems, that is why soft links exist.

```
man ln
```

---

