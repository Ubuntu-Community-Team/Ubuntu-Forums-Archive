---
title: "split a folder containing text files"
date: 2011-12-13
forum: General Help
---

### Post by coffeecake on 2011-12-13
hi all. I have a folder containing 100 text files. How can i write a shell script that takes all these files and split them ?

---

### Post by Lars Noodén on 2011-12-13
What do you mean by split?

---

### Post by coffeecake on 2011-12-13
i mean [http://unixhelp.ed.ac.uk/CGI/man-cgi?split](http://unixhelp.ed.ac.uk/CGI/man-cgi?split) .

---

### Post by Lars Noodén on 2011-12-13
You could use [find](http://manpages.ubuntu.com/manpages/oneiric/en/man1/find.1.html).

```

find */path/to/dir* -name '*.txt' -exec split "{}" \;

```

---

### Post by nothingspecial on 2011-12-13
> **Lars Noodén said:**
> You could use [find](http://manpages.ubuntu.com/manpages/oneiric/en/man1/find.1.html).

```

find */path/to/dir* -name '*.txt' -exec split {} \;

```

But you don't need to if they are all in the same directory

```
for f in *; do split "$f"; done
```

---

