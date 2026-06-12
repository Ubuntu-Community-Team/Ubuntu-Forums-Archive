---
title: "vim keyboard shortcuts not working"
date: 2010-12-14
forum: General Help
---

### Post by junggle on 2010-12-14
i'm trying to set up vim to move line up/down on pressing Alt-k/Alt-j
but it doesn't work (just blinks the screen and moves cursor up/down):

```

nnoremap <A-j> :m+<CR>==
nnoremap <A-k> :m-2<CR>==
inoremap <A-j> <Esc>:m+<CR>==gi
inoremap <A-k> <Esc>:m-2<CR>==gi
vnoremap <A-j> :m'>+<CR>gv=gv
vnoremap <A-k> :m-2<CR>gv=gv
```

the above worked for me in windows but it doesn't work in ubuntu.
any idea why?

this works in ubuntu:

```
nnoremap <C-S-j> :m+<CR>==
nnoremap <C-S-k> :m-2<CR>==
inoremap <C-S-j> <Esc>:m+<CR>==gi
inoremap <C-S-k> <Esc>:m-2<CR>==gi
vnoremap <C-S-j> :m'>+<CR>gv=gv
vnoremap <C-S-k> :m-2<CR>gv=gv
```

i'm using vim in default terminal, ubuntu 10:10

---

