---
title: "Braces automatically getting inserted in vim"
date: 2009-11-24
forum: General Help
---

### Post by samebchase on 2009-11-24
After opening a file using vim, and simply moving up and down using the j and k keys is causing what can be seen in the attached screenshot. This has happened several times before. Creating a new file and editing doesn't seem to be the problem, but opening an existing file sometimes causes this.
 
I am forced to :q immediately and then use Gvim to continue editing.

I also get the "Recover the .swp" file error message occasionally when trying to open a file.

I recently followed the advice in this link:

[http://ubuntuforums.org/showthread.php?t=23169&page=2](http://ubuntuforums.org/showthread.php?t=23169&page=2)

I don't want to have .swp files all over the folder in which I'm working in. Is there any alternative?

Can someone please advise what I need to do to fix this.

Here is my .vimrc:

```

colorscheme desert
set columns=207
set lines=38
set guifont=Monospace\ 14
set backupdir=/home/samuel/P/C/.vimswaps,/tmp
set ai
set nu
set tabstop=3
set shiftwidth=3
set syntax=C
map <F3> : call CompileGcc()<CR>
func! CompileGcc()
  exec "w"
  exec "!gcc % -o %<"
endfunc

map <F4> :call CompileRunGcc()<CR>
func! CompileRunGcc()
  exec "w"
  exec "!gcc % -o %<"
  exec "! ./%<"
endfunc

```

---

