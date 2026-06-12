---
title: "TexMaker issues"
date: 2009-11-13
forum: General Help
---

### Post by g.a. on 2009-11-13
Some Texmaker (ver 1.8 ) issues under Ubuntu 9.04:

- Is it possible to change the number of spaces for the tab key?

- When using the command "Quick Build", in case of a Latex error, Texmaker hangs. It is necessary to killall latex and the program continues working;

- The autocompletition disappears as soon as the first characters of the environment are typed. For example, if I'm in "\beg" the pop-up menu is there listing all the possibilities but as soon as I'm in "\begin{eq" there is not anymore. Is it normal?

- Is there a command/shortcut to close an opened environment? 

- Sometimes the prompt is missing and it is necessary to click with the mouse somewhere else (for example in the "structure" window) to make it appear back

Thanks,
g.

---

### Post by roquentin on 2009-11-17
> **g.a. said:**
> Some Texmaker (ver 1.8 ) issues under Ubuntu 9.04:

- When using the command "Quick Build", in case of a Latex error, Texmaker hangs. It is necessary to killall latex and the program continues working;



maybe you need the -interaction=nonstopmode option to [pdf]latex

details here:
[http://www.xm1math.net/texmaker/doc.html#SECTION02]("http://www.xm1math.net/texmaker/doc.html#SECTION02")

bye

---

### Post by g.a. on 2009-11-17
right thanks a lot

---

### Post by akvik on 2009-11-19
Unrelated post, 

but check out texmakerx, I've built it from svn (much better version) and I think it's the best latex editor around.

[http://texmakerx.sourceforge.net/](http://texmakerx.sourceforge.net/)

---

### Post by g.a. on 2009-11-20
well, not really unrelated. I just installed TexMakerX and it seems to be really efficient.

I have just installed the deb downloaded from sourceforge and used for few minutes. I'm impressed about the features.

Will it be part of the repository in future releases? 

best,
g.

---

### Post by akvik on 2009-11-25
Don't know,

but I recommend that you install the SVN version if you are familiar with how to do it - there's several new features in the SVN version that makes it even better. But if you are not used to compile with SVN, then maybe it's best to wait for the next release (it's really not that hard though, it's a matter of installing the right packages and issue some commands in the terminal).

---

