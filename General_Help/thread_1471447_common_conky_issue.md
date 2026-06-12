---
title: "common conky issue?"
date: 2010-05-03
forum: General Help
---

### Post by princeofnam on 2010-05-03
i installed conky, but when i executed the next command in terminal to begin setting it up and using it i get the following:

sushi@Tyr:~$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
gzip: /usr/share/doc/conky/examples/conkyrc.sample.gz: No such file or directory

and when i try to run conky...

sushi@Tyr:~$ conky
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
    This program is calling the Imlib call:

    imlib_context_free();

    With the parameter:

    context

    being NULL. Please fix your program.

---

### Post by ajgreeny on 2010-05-03
If you have not produced your own ~/.conkyrc file in home the program will use the example one as shown in the errors you see. You do not normally need to do anything as far as I remember, but the default only gives a simple output like my first screenshot.

By editing your own ~/.conkyrc you can get a much better output, eg. like my second screenshot.  The conkyrc.txt is also attached as you may find it helpful as a template to edit for your own system.

I hope this is helpful to you.

---

