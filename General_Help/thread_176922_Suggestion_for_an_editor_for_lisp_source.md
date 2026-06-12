---
title: "Suggestion for an editor for lisp source"
date: 2006-05-15
forum: General Help
---

### Post by dierre on 2006-05-15
I need to do a little coding in lisp...
can you please recommend an editor for it that runs under gnome?

I would like it to do:
- syntax highlighting
- parentheses balancing
- auto indenting

Unfortunately gedit doesn't do any of these for lisp. And (x)emacs really doesnt suit my tastes...

Thank you!

---

### Post by kabus on 2006-05-15
(g)vim 
syntax highlighting should work out of the box, you can tell vim to use lisp-style indenting by entering ':set lisp'.
Not sure  'parentheses balancing' is, but you can jump to matching parentheses with '%'. 
Parentheses pairs are also automatically highlighted in vim 7.

---

### Post by greshamp on 2007-04-06
This is an old question but I wanted to place a decent answer as it comes up quite high on google.

My recommendation is [EMACS + SLIME]("http://www.cliki.net/SLIME"). However all the useful editor/ide links are likely to be on the [Cliki]("http://www.cliki.net/IDE") and should remain updated. This does of course mean learning emacs keystrokes!! It's worth it.

To get this running on ubuntu, install the following packages:-
emacs
slime
cl-swank

cmucl
cmucl-clm
cmucl-source

You'll get a whole heap more dependencies.

---

