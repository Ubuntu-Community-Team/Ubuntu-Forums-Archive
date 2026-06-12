---
title: "annoying pidgin plugin"
date: 2010-08-07
forum: General Help
---

### Post by Someone uk on 2010-08-07
can someone explain how [this plugin](http://code.google.com/p/pidgin-nudge/) is supposed to be installed
i have found it very hard to find any relevant information....anywhere

---

### Post by Someone uk on 2010-08-07
no one?

---

### Post by Vaphell on 2010-08-07
open terminal and paste the following one by one (highlight here, middleclick in terminal)
```

sudo apt-get install subversion pidgin-dev build-essential
svn checkout http://pidgin-nudge.googlecode.com/svn/trunk/ pidgin-nudge-read-only
cd pidgin-nudge-read-only
make
sudo make install

```

1st one installs stuff to get the code from their repo (svn) and stuff required to compile it (pidgin-dev, build-essential)
second line - download code from svn
third line - go to the dir with the code
4th and 5th - compile the code and install the result

i have not tested this but it's a standard procedure when you get git/svn/cvs repository with the source code

---

### Post by Someone uk on 2010-08-07
thanks :)

---

### Post by charding on 2010-10-19
There are steps how to do this on the front page of the plugin under both Linux and Windows..

---

