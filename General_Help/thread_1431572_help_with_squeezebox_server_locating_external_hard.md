---
title: "help with squeezebox server locating external hard drive in ubuntu files"
date: 2010-03-16
forum: General Help
---

### Post by abdebban on 2010-03-16
I have a squeezebox server i am using with ubuntu 9.1 and cant find my external hard drive anywhere in the files to designate it as the source for my music scan. I am guessing it has something to do with ubuntu not having permission to read it or something. I am a complete novice at ubuntu so if you can give me simple steps to fix this problem i would really appreciate it.

---

### Post by soltanis on 2010-03-16
First of all, I don't know what squeezebox is, but this might just be a generic mount problem.

If you use Gnome, does a little icon pop up a few seconds after you plug in the drive? (KDE and Xfce have similar behavior, I think they open a file browser for the drive when it mounts).

Either way, please plug in the drive and post the output of
```

mount

```

Run from a terminal (Applications->Accessories->Terminal, type the command exactly as you see it, and use Ctrl+Shift+C to copy the text).

---

