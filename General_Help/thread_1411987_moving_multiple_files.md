---
title: "moving multiple files"
date: 2010-02-20
forum: General Help
---

### Post by 26venger on 2010-02-20
this is a noob question but how do i move multiple files at once using the command line?

---

### Post by kaibob on 2010-02-20
> **26venger said:**
> this is a noob question but how do i move multiple files at once using the command line?

The general command is along the lines of:

```
mv /home/kaibob/photos/* /home/kaibob/temp
```

To get more information concerning the mv command, enter the following in a terminal window:

```
man mv
```

See Glob Patterns on the following site for an explanation of the function of the * in the command line:

[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)

---

### Post by 26venger on 2010-02-20
thankz

---

### Post by joeknoodle on 2010-02-20
If you have a bunch of files, I recommend you copy them, then erase the originals. That way if something happens you lessen the risk of losing files.

---

### Post by 26venger on 2010-03-05
thanKZZZZ

---

