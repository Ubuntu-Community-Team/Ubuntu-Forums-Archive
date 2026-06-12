---
title: "cp link"
date: 2011-09-26
forum: General Help
---

### Post by bakegoodz on 2011-09-26
I have a symbolic link of a folder and I want to make a duplicate of the link and put it into another folder. How do I directly copy a link from the command line? I've tried ls -s, but I get the error "cp: omitting directory"

---

### Post by CatKiller on 2011-09-27
Why not just make a new symbolic link to your target directory?

---

### Post by seawolf167 on 2011-09-27
> **CatKiller said:**
> Why not just make a new symbolic link to your target directory?

Aye - this is what I came here to ask

```
man ln
```

---

### Post by WorMzy on 2011-09-27
> **bakegoodz said:**
> I've tried ls -s, but I get the error "cp: omitting directory"

Either you're getting your commands and outputs mixed up, or you've managed to replace the ls command with cp. To further confuse things, I think you meant to use ln, not ls.

ln = link
ls = list
rm = remove

Have you managed to mix up your commands, or did you just make a mistake while typing out the contents of your terminal?

Here's a tip: you can select text in gnome-terminal by using your mouse, then you can copy it by pressing Ctrl+Shift+C. You can then paste the copied text into anything you want (including web forums) as normal.

---

