---
title: "tree command does not display correctly"
date: 2011-12-14
forum: General Help
---

### Post by joopie18 on 2011-12-14
Hi folks

I am trying to get the tree command to work. I tried sudo apt-get tree and installing it (make, make install) from [ftp://mama.indstate.edu/linux/tree](ftp://mama.indstate.edu/linux/tree). Though the command does work, it does not display the results as wanted it does something like this:


&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;     &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; file.zip
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;     &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; file.xls
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; file.pdf
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; file.csv
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; file~

It does have the colouring, but I do not understand why the tabs or spaces are not displayed correctly.

Greetings
WC

---

### Post by supercheetah on 2011-12-14
What terminal app are you using?  That's usually the cause of problems like this.  I'm using Yakuake (based on Konsole) which displays *tree* just fine.

---

### Post by joopie18 on 2011-12-14
GNOME Terminal 2.30.2
Is this not the one most frequently used?

---

### Post by supercheetah on 2011-12-14
I just tried *tree* in Gnome Terminal 3.0.1, and it displayed just fine in there.  Try changing the font.  That could be an issue.

---

### Post by joopie18 on 2011-12-15
It was a font thing. Just changed the terminal to unicode...
Then it worked fine. 
Alternative solution: use tree -A
Thans a lot!

---

