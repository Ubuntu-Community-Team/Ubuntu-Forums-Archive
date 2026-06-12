---
title: "Not able to compile qjoypad in 10.04"
date: 2010-05-17
forum: General Help
---

### Post by Xenphor on 2010-05-17
Hello,

I'm trying to compile qjoypad but it gives me this error when I do ./configure:

./configure
./configure: line 4: pkg-config: command not found
Error: you will need libxtst to compile this program

I looked around and installed these programs:
sudo apt-get install qdevelop libxtst-dev

However, even after I installed them, I still receive the same error. What am I doing wrong?

---

### Post by BryanFRitt on 2010-05-23
Did you try [FONT="Courier New"]qt4-dev-tools[/FONT]?
[FONT="Courier New"]sudo apt-get install qt4-dev-tools[/FONT]

---

