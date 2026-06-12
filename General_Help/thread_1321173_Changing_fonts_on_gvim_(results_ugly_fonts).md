---
title: "Changing fonts on gvim (results ugly fonts)"
date: 2009-11-09
forum: General Help
---

### Post by geo909 on 2009-11-09
Hello all,

I am trying to use gvim here and I have a small problem. I want to change the default fonts. If you go to edit-> select font and choose *any*
font, the result will be an unnaturally ugly font. Even if you choose the default (sans, size 10), you'll get something extremely ugly.

Same results if you change the fonts by putting an entry like

```
set guifont=Sans\ 10
```
or
```
set guifont=monospace:s8
```

in .vimrc.

Let me demonstrate (note that I am selecting the same fonts
that are in the first screenshot!!):

[[IMG]http://www.picamatic.com/show/2009/11/10/04/35/5851956_bigthumb.png[/IMG]](http://www.picamatic.com/view/5851956_before/)

[[IMG]http://www.picamatic.com/show/2009/11/10/04/35/5851957_bigthumb.png[/IMG]](http://www.picamatic.com/view/5851957_selecting_font/)

[[IMG]http://www.picamatic.com/show/2009/11/10/04/35/5851959_bigthumb.png[/IMG]](http://www.picamatic.com/view/5851959_after/)


Any ideas?
Thanks in advance..

---

### Post by geo909 on 2009-11-11
Apparently only mono fonts look ok, I'll stick with them, there are many nice ones..

---

