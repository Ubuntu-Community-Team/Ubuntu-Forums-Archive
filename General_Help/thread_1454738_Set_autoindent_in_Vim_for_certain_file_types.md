---
title: "Set autoindent in Vim for certain file types"
date: 2010-04-15
forum: General Help
---

### Post by offbyone on 2010-04-15
I hope this is in the right spot. I need some help editing my .vimrc file. I want to edit it so that if I create a .cpp file, it will turn on cindent, and if I create a .asm file, it will turn on regular autoindent and set ft=nasm so Vim uses NASM syntax highlighting. How do I go about doing this?

Thanks!

---

### Post by rnerwein on 2010-04-15
hi
what to think about a build in function like
vim ()
{
  check out the ending of the file
  if asm --> move .vimrc.asm .vimrc
  else .....
...
/path_to_vim/vim $1
}
ciao

---

### Post by gmargo on 2010-04-15
_cpp/cindent solution:_

Easiest way is probably to use the "after" directory in your runtimepath. (See ":help after-directory" in vim on-line help.)

Create the file **$HOME/.vim/after/ftplugin/cpp.vim** (create intervening directories if necessary) with the content:
```

setlocal cindent

```_.asm/nasm/autoindent solution:_

Add the following to your $HOME/.vimrc:
```

augroup filetypedetect
    autocmd! * *.asm
    autocmd BufNewFile,BufRead *.asm setfiletype nasm|setlocal autoindent
augroup END

```

The astute observer will note these examples are really two ways to do the same thing.  More or less.

---

