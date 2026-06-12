---
title: "cat /etc/apt/sources.list"
date: 2012-02-13
forum: General Help
---

### Post by jerrrys on 2012-02-13
Why not nano or gedit or?  Just a curiosity.  I see cat used a lot and wonder if there is an advantage.

---

### Post by snowpine on 2012-02-13
**cat** is not an editor (like nano or gedit).

So we use cat a lot on the forums, when it is necessary to view the contents of a file, without editing said file. :)

**less** also works well for on-screen display of a file's contents.

---

### Post by WorMzy on 2012-02-13
cat just prints the contents of the file to standard output, gedit and nano are text editors.

Also, cat concatenates files (hence the name), so you can output the content of several files in one stream. It's useful for piping into another command, or joining a bunch of files together.

e.g.
```
cat /thisfile /anotherfile /a/faraway/file >> /theconcatinatedfile
```

```
cat /thisfile /anotherfile /a/faraway/file | sed 's:abc:def:g'
```

---

### Post by jerrrys on 2012-02-13
Thanks

There was/is a command that will also display line numbers when its posted (like to the forum).

I would love to find it again.  Any ideas?

---

### Post by Lars Noodén on 2012-02-13
**less** can display line numbers if you use **-N**

**cat** can too if you use [-n](http://manpages.ubuntu.com/manpages/oneiric/en/man1/cat.1.html)

---

### Post by jerrrys on 2012-02-13
Excellent.  Thanks to all

---

