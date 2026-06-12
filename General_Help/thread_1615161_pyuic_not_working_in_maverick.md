---
title: "pyuic not working in maverick"
date: 2010-11-06
forum: General Help
---

### Post by eantoranz on 2010-11-06
Hi!

I just created a couple of ui files on designer but then when I try to create the python code from them with pyuic I get almost no output. What's going on?

```

$ pyuic MainWindow.ui 
# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'MainWindow.ui'
#
# Created: sáb nov 6 15:40:33 2010
#      by: The PyQt User Interface Compiler (pyuic) 3.18.1
#
# WARNING! All changes made in this file will be lost!


from qt import *

```

Why is that?

---

### Post by kevin.krenz on 2010-11-25
I just ran into the same thing. Did you figure out what the problem was?

---

### Post by eantoranz on 2010-11-25
Not really. Haven't had the time to examine this problem. :-S

---

### Post by dino99 on 2010-11-25
[http://manpages.ubuntu.com/manpages/maverick/man1/pyuic.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/pyuic.1.html)

---

### Post by kevin.krenz on 2010-11-25
I suspect this may have something to do with the version of Qt being used. I tried out pyuic4, whose manpage specifically says that it is for Qt4, and it worked as expected.

---

