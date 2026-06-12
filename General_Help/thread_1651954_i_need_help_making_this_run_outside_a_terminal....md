---
title: "i need help making this run outside a terminal..."
date: 2010-12-24
forum: General Help
---

### Post by trevy on 2010-12-24
hey everyone i been looking at turtuals on Python,
  [http://www.youtube.com/watch?v=-lfWzPxOJQ8&feature=fvw](http://www.youtube.com/watch?v=-lfWzPxOJQ8&feature=fvw)

how do i publish its like he did on his desktop at the end

this is my code i run in the terminal 

#!/usr/bin/env python
x = raw_input("enter name: ")
print "hey " + x
raw_input("press<enter>")

---

### Post by Cheesehead on 2010-12-24
He didn't really 'publish' anything.
The black background is a terminal or command line window.
The white background is a development application (like idle or pywin). They can be much easier to use than the command line. Do try one.

---

### Post by nice_like_rice on 2010-12-24
I'm not sure exactly what you mean, but if you want a file you can double-click on you could do this:

Save your file as test.py.

So now if you double click on test.py it should come up in a text editor.

Go to the directory from the terminal, and type in "chmod +x test.py".

This with make it executable.

Now you should be able to run it by double-clicking then saying run, or by typing ./test.py in the terminal.

---

