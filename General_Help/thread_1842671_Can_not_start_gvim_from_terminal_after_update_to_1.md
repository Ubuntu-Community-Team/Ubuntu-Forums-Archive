---
title: "Can not start gvim from terminal after update to 11.04?"
date: 2011-09-11
forum: General Help
---

### Post by ablmf on 2011-09-11
I found that if I start gvim from terminal, the GUI of gvim can't be rendered. I can see switch to gvim with alt+tab, and I can type ":q" to close it, but I couldn't see anything.

I don't know why, but it suddenly came across that it might due to this line of code my vimrc

```

" Full Screen
autocmd GuiEnter * set lines=999 columns=999

```

Commenting it out will resolve the problem.  But now I will need find a new way to make gvim maximize automatically.

---

