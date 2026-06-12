---
title: "How do I save a copy of my bash entries/history?"
date: 2011-02-16
forum: General Help
---

### Post by maddbaron on 2011-02-16
Hello,

Need to back those up.

---

### Post by b0b138 on 2011-02-16
its the file ~/.bash_history

---

### Post by Rubi1200 on 2011-02-16
In your home folder, "Ctrl" + "H" to show hidden files. Then just open the file b0b138 pointed you to , copy contents to a new file, save somewhere safe.

---

### Post by maddbaron on 2011-02-16
ohhhh ok thanks very much... would anyone also know how to save a copy of what programs I currently have installed in a list form?

---

### Post by nothingspecial on 2011-02-16
```
dpkg --get-selections > installed.txt
```

---

### Post by maddbaron on 2011-02-16
> **nothingspecial said:**
> ```
dpkg --get-selections > installed.txt
```

thank you!

---

### Post by t0p on 2011-02-16
Just in case you don't know, the above command will put a list of programs into a file called *installed.txt*.  Also, it might be a good idea to check out the man page for dpkg; ie run

```

man dpkg

```

otherwise the contents of *installed.txt* might seem a little confusing.

---

### Post by Rubi1200 on 2011-02-16
> **maddbaron said:**
> ohhhh ok thanks very much
No problem, you are more than welcome :-)

---

