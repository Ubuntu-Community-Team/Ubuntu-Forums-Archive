---
title: "word wrap in vim"
date: 2012-02-01
forum: General Help
---

### Post by subhojit on 2012-02-01
how to enable word wrap on vi editor?

---

### Post by maverickaddicted on 2012-02-01
I do not know much about the command, but I think```
:set wrap
``` will do the trick for you.
If that works you can make this setting permanent by editing vimrc file.
You can get more information about vimrc file -

[http://vim.wikia.com/wiki/Vimrc](http://vim.wikia.com/wiki/Vimrc)

---

### Post by Khayyam on 2012-02-01
> **subhojit said:**
> how to enable word wrap on vi editor?
I assume you mean line breaks, as text will "wrap" according to the width of your terminal. By defualt vim sets 'textwidth=0' , which means that without a 'return' the line is as long as the number of chars typed. If you want an automatic line return then set the value of textwidth to a value suitable for your terminal. eg:

set tw=80

You could also set the value dependent on filetype, eg:

autocmd BufRead *.txt set tw=80
autocmd BufRead *.html set tw=0

see:

:help textwidth
:help wrap

HTH

---

### Post by subhojit on 2012-02-02
> **maverickaddicted said:**
> I do not know much about the command, but I think```
:set wrap
``` will do the trick for you.
If that works you can make this setting permanent by editing vimrc file.
You can get more information about vimrc file -

[http://vim.wikia.com/wiki/Vimrc](http://vim.wikia.com/wiki/Vimrc)

thanks :)

---

