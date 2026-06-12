---
title: "how to find the file a launch icon starts?"
date: 2012-05-02
forum: General Help
---

### Post by kurja on 2012-05-02
In windows I can right-click an icon or a start menu item to find out what file it's launching, and where that file is; how would I achieve this in Ubuntu?

---

### Post by kurja on 2012-05-03
bump.

---

### Post by Cheesemill on 2012-05-03
Take a look in /usr/share/applications/ to find the correct launcher, right-click on it and look at it's properties to find the command that it launches (for example the Firefox launcher runs the command firefox).

To find the full path you can then use the which command in a terminal:
```
rob@quantal:~$ which firefox
/usr/bin/firefox
```

---

### Post by kurja on 2012-05-03
that's.... er, a hyper-complicated way to find out where a shortcut leads to.

thanks though.

---

### Post by Cheesemill on 2012-05-03
> **kurja said:**
> that's.... er, a hyper-complicated way to find out where a shortcut leads to.

thanks though.

Well let us know if you have a quicker way then.

---

### Post by kurja on 2012-05-04
> **Cheesemill said:**
> Well let us know if you have a quicker way then.
Sure, I'll let you know if I ever find an easier way.

I'm still fairly new to ubuntu/linux, and this is one of the basic things that seem difficult in comparison to microsoft systems - finding where a program's files are.

---

### Post by Cheesemill on 2012-05-04
If you want to know the basics behind the Linux file system, and why particular things are stored in a particular location then here are a couple of links for you:

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure](http://www.thegeekstuff.com/2010/09/linux-file-system-structure)
[http://www.tuxradar.com/content/take-linux-filesystem-tour](http://www.tuxradar.com/content/take-linux-filesystem-tour)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.freeos.com/node/36](http://www.freeos.com/node/36)

---

