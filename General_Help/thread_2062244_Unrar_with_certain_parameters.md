---
title: "Unrar with certain parameters"
date: 2012-09-24
forum: General Help
---

### Post by KnockerDolt on 2012-09-24
Hi,
I've got about 1000 RAR files with multiple files in them. Is it possible to extract just the newest file from each RAR file instead of extracting them one by one and selecting the newest file? I'm a bit of a greenhorn with linux. I'm fairly sure it could be done in the terminal but I wouldn't have a clue where to start :(.

---

### Post by rai4shu2 on 2012-09-25
If you have rar installed, you could try:

```
rar x *.rar
```

You won't get just the newest files, though. For that, you'll have to sort by modification date in your file browser.

---

### Post by newb85 on 2012-09-25
Sounds to me like you'll need to write a script with a loop.

Pull up the man page for unrar to figure out how to have your loop figure out which is the newest.  I think there's an option for a verbose listing.

Man page by entering

```
man unrar
```

There are many tutorials on writing shell scripts and for loops.  Do some searching and reading, try your hand at it, and post any questions/problems you run into.

---

