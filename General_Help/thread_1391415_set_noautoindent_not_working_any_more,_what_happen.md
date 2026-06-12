---
title: "set noautoindent not working any more, what happened? am I crazy?"
date: 2010-01-26
forum: General Help
---

### Post by jzacsh on 2010-01-26
in my ~/.vimrc I have the following
```
" this is vim's rc
" comments in double-quotes (`"')
" awesome reference:            http://amix.dk/vim/vimrc.html

set history=400
set autoindent
set nosi *" placed here because of this new autoindent issue*
set ruler
set number
set mouse=a

set cmdheight=2

set background=dark
colorscheme zellner

" set which wraps
set whichwrap+=<,>,h,l

" for filetype event-based configs
filetype plugin on
filetype indent on

"read in live edits on opened files
set autoread

" vim's extra set of commands
" are incompatible with vi
set nocompatible

" show results while typing
set incsearch

" text wrap:
" set wrapmargin=80

```

I've been using vim for probably almost 6 months. I always copy text to GNUscreen's buffer and paste it into vim, right after doing the following:
```
:set noai
--or--
:set noautoindent
```

This has always worked -- now (*just today, right this moment*) the above two commands don't work. I'm typing the above command and even while just trying to type normally (no pasting) vim is *still* indenting! What's going on? Some new update in vim I should be aware of? -- I know I certainly haven't edited my ~/.vimrc file anytime recently (*aside from the `set nosi`*)

---

