---
title: "how does filename gets mapped to its inode"
date: 2010-03-10
forum: General Help
---

### Post by siddheshbade on 2010-03-10
Hi, i am trying to make a system call which would return a particular field of the inode structure of a file.For this reason i want to fetch the whole of inode structure of the given filename.Is there a way to do the same????

---

### Post by dcstar on 2010-03-11
> **siddheshbade said:**
> Hi, i am trying to make a system call which would return a particular field of the inode structure of a file.For this reason i want to fetch the whole of inode structure of the given filename.Is there a way to do the same????
This will give you the inode number of a file, after that I don't know:
```
ls -i
```

---

### Post by capscrew on 2010-03-11
> **siddheshbade said:**
> Hi, i am trying to make a system call which would return a particular field of the inode structure of a file.For this reason i want to fetch the whole of inode structure of the given filename.Is there a way to do the same????

*"stat() is a Unix system call that returns useful data about a file inode." *[SIZE="1"]**Wikipedia**[/SIZE]

Here is what [**_[COLOR="Blue"]Wikipedia [/COLOR]_**]("http://en.wikipedia.org/wiki/Stat_(Unix)")as to say about the [FONT="Courier New"]stat() routines.[/FONT]

Edit: Here is what Wikipedia has to say about the term *inode *itself.
[_[COLOR="Blue"]http://en.wikipedia.org/wiki/Inode[/COLOR]_]("http://en.wikipedia.org/wiki/Inode")

---

