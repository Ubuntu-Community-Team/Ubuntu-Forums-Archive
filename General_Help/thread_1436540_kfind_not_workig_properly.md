---
title: "kfind not workig properly"
date: 2010-03-22
forum: General Help
---

### Post by lovinglinux on 2010-03-22
I have KDE 4.4 from the backports PPA.

kfind is not working properly when searching for Contents. Sometimes it finds just a couple of results, sometimes it finds nothing. I know the files have the selected containing text. For instance, it finds a string in two dtd files, while it should also have found it on two js files under the same directory tree.

Additionally, when I delete files from kfind, the list is not refreshed automatically as it used to do in KDE 4.3.

This is driving me crazy, because I'm doing a lot of programming this week and need to find strings on several files.

Anyone else experiencing this issue? Any fix? 

What alternative application for KDE I could use?

---

### Post by 0e8h on 2010-03-24
Same problem.  Checking bugs, the fix is done for KDE 4.4.2 which will be released on 30th March, 2010.

It's crazy that this wasn't repaired for current KDE as it's a vital feature for developers.

---

### Post by 0e8h on 2010-03-24
> **lovinglinux said:**
> What alternative application for KDE I could use?

Nope none.  I tried Gnome and it's so crummy and basic compared to KDE.  There doesn't even seem to be a content search for Gnome.

---

### Post by 0e8h on 2010-03-24
Krusader file utility may get you over the time.  It works and will allow you to pick up files in gfx, opposed to finding files using command line.

---

### Post by lovinglinux on 2010-03-24
> **0e8h said:**
> Same problem.  Checking bugs, the fix is done for KDE 4.4.2 which will be released on 30th March, 2010.

It's crazy that this wasn't repaired for current KDE as it's a vital feature for developers.

Thanks for the info. I hope it gets into the backports ppa.

> **0e8h said:**
> Krusader file utility may get you over the time.  It works and will allow you to pick up files in gfx, opposed to finding files using command line.

Thanks. It works well, although it's a full replacement for dolphin, which I prefer. Anyway, it will be useful until the bug in kfind is fixed.

---

