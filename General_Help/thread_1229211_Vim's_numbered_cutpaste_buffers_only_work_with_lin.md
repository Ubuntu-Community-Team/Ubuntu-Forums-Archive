---
title: "Vim's numbered cut/paste buffers only work with lines"
date: 2009-08-01
forum: General Help
---

### Post by Unknown 4242 on 2009-08-01
For some reason my install of vim only keeps whole lines in the numbered cut/paste buffers.  What do I need to adjust in my Vimrc to get the normal behavior back?

My ~/.vimrc

" Options Taken For Granted "
set nocompatible
set showcmd
set showmode

set smartindent
set backupext=~
set incsearch
set ic

" Show autocomplete menus
set wildchar=<Tab>
set wildmenu

"Options for basic programming help
set foldmethod=indent
syntax on

"Apperance Options
colorscheme desert

" Bind ctrl-s to write
nmap <c-s> :w<CR>
imap <c-s> <Esc>:w<CR>a

" Easy tab motion
nmap <C-j> :tabp <CR>
nmap <C-k> :tabnext <CR>

" Cycle through windows in a tab from top to bottom/left to right
nmap <C-h> :wincmd w <CR>

---

