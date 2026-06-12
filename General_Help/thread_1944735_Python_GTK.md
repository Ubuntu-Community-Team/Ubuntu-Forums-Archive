---
title: "Python GTK"
date: 2012-03-21
forum: General Help
---

### Post by High Camp on 2012-03-21
Hi All,

I wanted to post this here and get some feedback before talking to the people over at Python/GTK and potentially getting laughed at.

Long story, I'm working through the Learn Python The Hard Way tutorials. I was being all slick and made a current.py file. I'm doing each exercise in that file. I also made a copy.py file that asks which exercise number and copies current.py to EXERCISE#.py. That was working great but I'm also too lazy to remember which exercise I'm on so created a file called link.py that asks which exercise I'm on and then puts the link to that on the clipboard. The contents of those files don't really matter although I'll share them if anyone wants.

Long story short, the copy.py file was being included each time I ran link.py. I spent a bunch of time debugging and narrowed it down to the 'import gtk' line (you have to import it to access the clipboard) in link.py. I followed that too and assumed I had done some damage to the Python modules. 

Anyway, I finally figured out by pure luck, that when you 'import gtk' it includes any file in the current folder named copy.py. I replicated this behaviour on 2 different computers running Xubuntu and Ubuntu respectively. The question is, is this a bug or done on purpose for some reason? Should it be documented to save someone else spending as much time as I did debugging?

To replicate this yourself, do the following:
[LIST=1]
[*]Create a folder, let's call it '~/test'
[*]create a file '~/test/copy.py'
[*]in copy.py put 'print "copy.py"'
[*]create another file called 'test.py'
[*]in test.py put "import gtk"
[*]Open a terminal to ~/test and type 'python test.py', it'll output "copy.py" and create a file copy.pyc
[/LIST]

Any feedback would be appreciated, thanks.

---

### Post by ksa618 on 2012-03-21
Here's your clue:
```
File "/usr/lib/python2.7/gettext.py", line 49, in <module>
    import locale, copy, os, re, struct, sys
...
File "/usr/lib/python2.7/xml/dom/xmlbuilder.py", line 3, in <module>
    import copy
```

Gtk is trying to import copy, and since you have a local module called copy, it will import that instead of the correct one.

---

