---
title: "Open directory via terminal?"
date: 2012-09-18
forum: General Help
---

### Post by ChaosChris2009 on 2012-09-18
I want to be to open these common directories via terminal: videos, downloads, music, pictures, documents

What would the terminal commands be?

Like if I run the command in terminal, I want it to open the directory in Nautilus

---

### Post by Kirk Schnable on 2012-09-18
```
nautilus ~
```
Will open your home folder in Nautilus.

```
nautilus ~/Desktop
```
Will open /home/YOURUSER/Desktop.

From here, I'd suspect you can extrapolate the pattern.

Kirk

---

### Post by Jagoly on 2012-09-18
Just thought I'd add, if you want it to open, but still be able to use that terminal, you can use, for example your home directory: ```
nautilus ~ &
```
just put an & at the end.

---

