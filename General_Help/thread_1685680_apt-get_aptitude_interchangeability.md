---
title: "apt-get aptitude interchangeability"
date: 2011-02-11
forum: General Help
---

### Post by Wangberg on 2011-02-11
this may be reoccurring, but everything i find is dated.  

are apt-get and aptitude, at the time of this post, interchangeable? 

ie.  can i use them both for package management synonymously?

---

### Post by pmlxuser on 2011-02-11
basically yes ...they are interchangeable with a few differences..

---

### Post by Wangberg on 2011-02-11
> **pmlxuser said:**
> basically yes ...they are interchangeable with a few differences..

will they "break" each other or screw up dependencies if used interchangeably?

---

### Post by WorMzy on 2011-02-11
aptitude isn't installed by default, so you're probably best off sticking with apt-get unless you manually install aptitude.

aptitude is more or less a console version of Synaptic Package Manager with an ncurses UI, whereas apt-get is just a bunch of functions (install, remove, purge, etc).

---

### Post by nothingspecial on 2011-02-11
There used to be problems a few years back, can`t remember the details but I know it was advised to use one or the other. Haven't come across the subject for ages though.

---

### Post by treesurf on 2011-02-11
I use them both interchangeably and have never had any issues because of it.

---

### Post by gmargo on 2011-02-11
**aptitude**, when given arguments, acts almost exactly like **apt-get**.  Without arguments it starts a curses gui interface similar to the old **dselect** interface.  Personally I prefer **aptitude** because it handles conflicts much better - it will provide interactive choices on various ways to solve problems.  I only use **apt-get** for the 'source' command, which **aptitude** curiously lacks.  Your best bet is to start reading the man pages and get familiar with both.

---

