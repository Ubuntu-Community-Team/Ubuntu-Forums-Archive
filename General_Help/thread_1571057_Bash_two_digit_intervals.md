---
title: "Bash: two digit intervals?"
date: 2010-09-09
forum: General Help
---

### Post by mirshafie on 2010-09-09
Hi folks,
Is it possible to point to a two-digit interval with regular experssions?

Background:
I'm using mplayer to watch tv shows, that often have episode numbers in their names. I know how to easily add several files to the playlist by using brackets, by typing something like
[FONT="Fixedsys"]$ mplayer tv/South.Park.S1.E0[1-5]*avi[/FONT]

**Is there a way to point to files 06-13 in a single expression?**

---

### Post by slakkie on 2010-09-09
```

$ ls Big\ Bang\ Theory\ S01E{0[7-9],1[0-3]}*
$ ls Big\ Bang\ Theory\ S01E{06..13}*

```

---

### Post by mirshafie on 2010-09-09
Awesome! Thank you very much.

---

