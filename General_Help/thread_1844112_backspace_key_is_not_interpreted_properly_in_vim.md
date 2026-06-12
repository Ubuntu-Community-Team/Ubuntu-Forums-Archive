---
title: "backspace key is not interpreted properly in vim"
date: 2011-09-14
forum: General Help
---

### Post by c0ldfusi0nz on 2011-09-14
Just made a fresh install of 11.04 on a new machine and have run into the common problem that using the backspace key in insert mode outputs "^?" rather than deleting characters. I've tried the recommended fixes without success.

My .vimrc has both:
set nocompatible    " Use Vim defaults (much better!)
set backspace=2        " allow backspacing over everything in insert mode

and I have checked that it's running in nocompatible mode via ":set compatible?" to which I get the response "nocompatible"

It looks like vim-full is no longer a valid package, so I also installed vim-gnome, to no avail. Have I missed something?

---

### Post by kimda on 2011-09-14
Hi. I have no problems with the backspace in insert mode also I' ve got these same settings like you. It seems like you are missing some packages. These are the packages that I have installed. 

vim
vim-common
vim-runtime
vim-tiny

---

### Post by c0ldfusi0nz on 2011-09-14
Hm, I have all of those installed. I have:

vim
vim-common
vim-tiny
vim-runtime
vim-gui-common

---

### Post by haqking on 2011-09-14
[fix backsapce and delete problems in vim]("http://vim.wikia.com/wiki/Backspace_and_delete_problems")

---

### Post by c0ldfusi0nz on 2011-09-14
Apparently it's not a bad mapping. 

:fixdel prevents it from outputting "^?" but it still doesn't erase characters... 

The only thing I see left to try that isn't insanely complicated is defining a Backspace function, but of course the help doc makes no mention of where you place this vimscript in order for .vimrc to pick it up...

---

### Post by haqking on 2011-09-14
> **c0ldfusi0nz said:**
> Apparently it's not a bad mapping. 

:fixdel prevents it from outputting "^?" but it still doesn't erase characters... 

The only thing I see left to try that isn't insanely complicated is defining a Backspace function, but of course the help doc makes no mention of where you place this vimscript in order for .vimrc to pick it up...

Edit: dont think that is used anymore

---

