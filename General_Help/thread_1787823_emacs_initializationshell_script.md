---
title: "emacs initialization/shell script"
date: 2011-06-21
forum: General Help
---

### Post by A Feyn Man on 2011-06-21
I have emacs23 from the Lucid repository.
I know how to load and edit remote python files with

```
 C-x C-f  /ssh:usr@domain:/directory/*.py 
```

Since I use this same command every time I open emacs, and I see that you can use lisp commands and can also edit the ~/.emacs  init file, I know that there is some launcher or shell script I can write to open emacs and run that one line at startup.

Help please?

---

### Post by gunksta on 2011-06-28
Sounds like you need to learn how to create some simple emacs macros.

[http://www.emacswiki.org/emacs/KeyboardMacros](http://www.emacswiki.org/emacs/KeyboardMacros)

---

### Post by furtypajohn on 2011-06-29
Add the following line to your ~/.emacs file, of course, substituting the file you actually want to open.

```
(find-file "~.emacs")
```

---

