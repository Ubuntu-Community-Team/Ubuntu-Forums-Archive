---
title: "Very wierd..."
date: 2010-05-12
forum: General Help
---

### Post by oohbuntoo on 2010-05-12
I can't find my (.) folders.  LIke for example:

*[COLOR="Red"]/home/(your name)/.local/share/vlc/vlcsnap-2010-05-11-11h25m32s249.png[/COLOR]*

I can't find the .local folder.

I don't know what I am doing wrong.

---

### Post by John Bean on 2010-05-12
Have you opted to view hidden files/folders (Ctrl+H in Nautilus)?

---

### Post by iponeverything on 2010-05-12
```
ls -a | grep ^\\.
```

Run this from inside of your home directory to just show just the hidden.

---

### Post by oohbuntoo on 2010-05-12
> **John Bean said:**
> Have you opted to view hidden files/folders (Ctrl+H in Nautilus)?

[FONT="Garamond"][COLOR="Green"]Good job!  I must've been high one day and hit Ctrl+h.  Thanks.  I feel dumb, yet educated.[/COLOR][/FONT]

---

