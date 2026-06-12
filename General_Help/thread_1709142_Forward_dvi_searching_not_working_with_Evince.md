---
title: "Forward dvi searching not working with Evince"
date: 2011-03-17
forum: General Help
---

### Post by aryzing on 2011-03-17
I was going through the latex suite for vim tutorial and it asked me to perform a forward search with the command \ls after having compiled .tex file and having introduced these two commands:


```

:let g:Tex_CompileRule_dvi = 'latex -src-specials -interaction=nonstopmode $*'

:TCTarget dvi

```

The result is the vim editor displaying the following message at the bottom of the screen

:call Tex_ForwardSearchLaTeX()

but nothing happens. Has anyone had a similar problem?

Thanks

---

### Post by sysrin0 on 2011-05-05
I ran into the same problem, since there are some problems in the configuration settings(in file *~/.vim/ftplugin/tex.vim*) 
```

let g:Tex_ViewRule_dvi="xdvi -editor 'gvim --servername latex-suite --remote-silent'"

```

by debugging the *vim*, I find that the problem lies in the function [FONT="Courier New"]Tex_ForwardSearchLaTeX()[/FONT] which is defined in file *~/.vim/ftplugin/latex-suite/compiler.vim*

the statement on about line 400th of file *compiler.vim*
```
let execString = 'silent! !'.viewer.' "'.mainfnameRoot.'.'.s:target.'" '.line('.').' "'.expand('%').'"'
```
should be amended to 
```
let execString = 'silent! !'.viewer.' -sourceposition '.line('.').expand("%:r").' '.mainfnameRoot.'.dvi'
```

then,the problem is solved when you restart *vim*.

---

