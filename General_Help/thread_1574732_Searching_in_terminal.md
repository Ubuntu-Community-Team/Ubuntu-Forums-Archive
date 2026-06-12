---
title: "Searching in terminal"
date: 2010-09-14
forum: General Help
---

### Post by Aginor95 on 2010-09-14
Hi.

I want to use the terminal to search for all files (also the hidden ones) who are not of a specified type.

For example; I want to find all files that do not end with *.txt.

How do I do this?

Thanks from Norway.

---

### Post by JK3mp on 2010-09-14
Try this. =)

```
man find
```

---

### Post by Aginor95 on 2010-09-14
> **JK3mp said:**
> Try this. =)

```
man find
```

Thanks for the answer.

I tried that, but I found no way of searching for files NOT of a particular type. Though I have to admit not reading all the documentation.

---

### Post by WorMzy on 2010-09-14
```
sudo updatedb && locate <filename>
```

---

### Post by Aginor95 on 2010-09-14
> **WorMzy said:**
> ```
sudo updatedb && locate <filename>
```

But is there some way I can tell the computer to find all files not of a particular type.

For example; find all files not ending with .stat in some specified directory?

---

### Post by raafaell on 2010-09-14
> find / -iname '*htm' -o -iname '*.html'


try that..

---

### Post by Aginor95 on 2010-09-14
> **raafaell said:**
> try that..

Seems close. But I can't get it to limit the search to a particular directory. It goes through all files on the computer. What to do?

---

### Post by JK3mp on 2010-09-14
oook... well you should. But ...

[Easy Find Tutorial]("http://content.hccfl.edu/pollock/unix/findcmd.htm")

Oh and this might be a little more organized if ya trust wikipedia...

[http://en.wikipedia.org/wiki/Find]("http://en.wikipedia.org/wiki/Find")

Find is really a useful command so you should read it too the fullest can FIND alot =).

---

### Post by raafaell on 2010-09-14
> **Aginor95 said:**
> Seems close. But I can't get it to limit the search to a particular directory. It goes through all files on the computer. What to do?

> find $'foldername' -iname '*htm' -o -iname '*.html'

that should do it.

---

### Post by andrew.46 on 2010-09-15
Hi Aginor,

> **Aginor95 said:**
> For example; I want to find all files that do not end with *.txt.

Perhaps this is what you are after:

```
find $HOME ! -iname '*.txt'
```

Andrew

---

