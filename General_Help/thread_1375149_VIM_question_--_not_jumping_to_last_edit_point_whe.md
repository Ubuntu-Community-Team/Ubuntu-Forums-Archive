---
title: "VIM question -- not jumping to last edit point when opening a file"
date: 2010-01-07
forum: General Help
---

### Post by n6ld on 2010-01-07
This is just a mildly irritating thing when using vim. on other systems (centos, redhat etc), vim jumps to the last edit point when opening a previously edited file. it does not on ubuntu. it always starts on the first line.

i have been through most of the faq's here and many other places, but can find no reference to this. the .viminfo file appears to be correct; the last edit point is duly recorded. i can find to reference to this behaviour in any of the forums, and nothing of note in the rc files.

does anybody know if there is an option to be set to enable this? it is not a show stopper and will not stop me from using vim, but it a nice feature.

also, i have read the various tirades about vim in the forums. i have been using UNIX for over 30 years (and many of the various flavors of linux), and have nothing but praise for vi (or vim). when you bounce around between various systems, you do not always know which editors are installed, but you always can rely on vi being there; the basic mechanisms have not changed over the years (but vim has added many nice features). even if you do not like it, it will be worth your time to learn its basics.

---

### Post by DaithiF on 2010-01-07
try adding this to your .vimrc file:
```
:au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g`\"" | endif
```

---

### Post by n6ld on 2010-01-08
> **DaithiF said:**
> try adding this to your .vimrc file:
```
:au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g`\"" | endif
```
Most excellent! works like a charm. kudos to you! Thanks.

---

### Post by dabrue on 2010-02-20
Thank you! I'd been trying to figure this out for a while

---

