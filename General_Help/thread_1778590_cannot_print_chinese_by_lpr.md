---
title: "cannot print chinese by lpr"
date: 2011-06-09
forum: General Help
---

### Post by six648 on 2011-06-09
I can see and edit chinese file in console by 
vi testfile

I also can gedit the testfile and print it in chinese perfectly.

But I can't see the chinese by cli to print file , can only see some small rectangles to instead.
lpr testfile

---

### Post by dandnsmith on 2011-06-09
Sounds like gedit has some filtering associated with the print function and the chinese characters.
I don't know much about gedit, but would look in the man pages to see if the options include a way to invoke the print from the command line.

---

