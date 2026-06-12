---
title: "vim"
date: 2010-04-11
forum: General Help
---

### Post by nischalinn on 2010-04-11
I've installed VIM but I can't open it. I've done the command:

**sudo apt-get install vim**

and it was instaled but now I cant open it,why?

---

### Post by mhgsys on 2010-04-11
vim is not a gui editor;

You can open it in a terminal with 
```
vi
```

[http://www.manpagez.com/man/1/vim/](http://www.manpagez.com/man/1/vim/)

---

### Post by gmargo on 2010-04-11
**Vim** has both gui and non-gui parts.  Install the **vim-gtk** package and you will be able to run "**gvim**" for the gui version. "**vim**" will still work on the command line.

---

