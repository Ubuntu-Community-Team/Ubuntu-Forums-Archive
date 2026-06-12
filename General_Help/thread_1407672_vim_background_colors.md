---
title: "vim background colors?"
date: 2010-02-15
forum: General Help
---

### Post by DrBloodmoney on 2010-02-15
I was hoping someone could help me with setting colors/colorschemes on vim.  I'm trying to get back into using vim, because Eclipse (and Pydev) just aren't cutting it for me anymore.

Ubuntu 9.04, vim upgraded via apt-get to vim-full

The terminal background color is overriding background choice.  Currently my terminal profile color is set to use the system background (which is white).

If I do :set background=dark the background does not change.  If I set it to a colorscheme with a dark background it does not change.  However, if I :set colorscheme blue, the background changes accordingly. Basically I'd like to keep my terminal white, and then use a dark colorscheme in vim.

Current .vimrc:
```
set background=dark
syntax on
colorscheme ir_black
set t_Co=256
```

Any ideas?

---

### Post by RHTopics on 2010-02-15
Here is an option for you, use "gvim" which is the gui version of vim.

You can use it just like vim from a terminal window, plus it has a Color Scheme option available under Edit from the menu bar.

If you are using Ubuntu then you will need to install the "vim-gnome" package, which will also require the "vim-gui-common" package.

---

### Post by DrBloodmoney on 2010-02-15
Thank you. I suppose I will just use gvim.

---

