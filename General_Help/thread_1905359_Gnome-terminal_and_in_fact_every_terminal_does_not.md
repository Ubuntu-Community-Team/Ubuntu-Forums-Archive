---
title: "Gnome-terminal and in fact every terminal does not display monospace fonts correctly"
date: 2012-01-06
forum: General Help
---

### Post by kirilp on 2012-01-06
Hi , 
I was just wondering why non of the terminals ( for example gnome-terminal ) are 
rendering non fixed-width fonts properly like other programs such as gedit and nautilus?
For reference purposes I have attached a picture using Purisa font with  terminal/gedit/nautilus  notice how in the terminal the spacing between letters is messed up such that it is hard to read. especially the sequences of Dr, me, Do (pretty much anny letter after D or M). Is there a way to display this fonts properly ? 
Thanks.

---

### Post by cortman on 2012-01-06
> **kirilp said:**
> Hi , 
I was just wondering why non of the terminals ( for example gnome-terminal ) are 
rendering non fixed-width fonts properly like other programs such as gedit and nautilus?
For reference purposes I have attached a picture using Purisa font with  terminal/gedit/nautilus  notice how in the terminal the spacing between letters is messed up such that it is hard to read. especially the sequences of Dr, me, Do (pretty much anny letter after D or M). Is there a way to display this fonts properly ? 
Thanks.

Hm... I guess I didn't even know the terminal supported other fonts. I don't know that there is a fix for this; the terminal really hasn't been engineered for good looks.

---

### Post by xyzzyman on 2012-01-06
Because it's a terminal... If you run a command like 'ls -l' to top or anything ncurses, they would break. Almost everything in the terminal is expecting rows/columns and fixed-with fonts are necessary for this.

---

### Post by dcstar on 2012-01-07
> **xyzzyman said:**
> Because it's a terminal... If you run a command like 'ls -l' to top or anything ncurses, they would break. Almost everything in the terminal is expecting rows/columns and fixed-with fonts are necessary for this.

Correct, and the Title of this thread is totally wrong. The Terminal *does* displaying fixed-width ("monospace") fonts correctly, it cannot display variable-width fonts in columns.

---

### Post by kirilp on 2012-01-07
Hi all , thanks for the quick reply's , your answers make sense and I did make a typo in the name of the thread.

---

### Post by kirilp on 2012-01-11
By the way I found a terminal that does render variable width font correctly
here is the link [http://software.jessies.org/terminator/#downloads](http://software.jessies.org/terminator/#downloads)

---

