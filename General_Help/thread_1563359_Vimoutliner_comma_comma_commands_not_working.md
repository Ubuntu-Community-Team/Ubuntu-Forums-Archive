---
title: "Vimoutliner comma comma commands not working"
date: 2010-08-29
forum: General Help
---

### Post by eihli on 2010-08-29
I spent a couple hours fighting this so I figured I'd post it so it would get indexed by google and might help someone else having this problem.

Here is the problem:

I installed vimoutliner using:
apt-get install vim-vimoutliner

I then ran the addon:
vim-addons install vimoutliner

I was then able to open .otl files and syntax worked fine, but the comma comma (,,) commands weren't working.

Every google search resulted in things about "maplocalleader" being set to "\" in Debian based releases. I went through my ~/.vim/ftplugin/vo_base.vim file and my /etc/vim/vimoutlinerrc file and changed the "let maplocalleader = ",,"" to "\" and uncommented it and added it to my .vimrc file and tried tons of other **** that I knew wouldn't work.

Anyway... to wrap things up.

```
filetype plugin indent on
```

I added that to my .vimrc and now the commands are working.

I hope this helps someone.

---

