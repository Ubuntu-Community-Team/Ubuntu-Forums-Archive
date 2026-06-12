---
title: "Vim syntax highlighting broken after upgrade"
date: 2009-07-03
forum: General Help
---

### Post by fishyboy on 2009-07-03
Hello all,

A few weeks ago I upgraded to Ubuntu 9.04, and ever since Vim does not highlight source code. I've tried obvious things like ":syn on", and I've also removed and reinstalled all vim-related things using aptitude. But I'm still stuck with one colour. Oh yes, I'm talking about the terminal version of Vim, although I've just tried GVim and that also has no syntax highlighting.

Does anyone know how I can restore Vim's syntax highlighting?

Cheers.

---

### Post by DaithiF on 2009-07-03
Hi, try installing the package vim-full

---

### Post by Elfy on 2009-07-03
:syntax on

apparently ;)

---

### Post by fishyboy on 2009-07-04
> **DaithiF said:**
> Hi, try installing the package vim-full

Oh yes, I forget to mention that vim-full is the package I'm using.

Here are all the vim-related packages I've got installed:

vim-common
vim-gnome
vim-gui-common
vim-runtime
vim-full

Thanks.

---

### Post by fishyboy on 2009-07-04
> **forestpixie said:**
> :syntax on

apparently ;)

I think that's the same as ":syn on"? Anyway, ":syntax on" doesn't help either. My guess is I'm probably missing the files with the syntax info, or I've got them but vim can't find them for some reason?

Cheers.

---

### Post by storeofjerks on 2009-07-14
Hi, I'm having the same problem, but on a new install of 8.10.  I removed vim-tiny, and installed:

vim
vim-runtime
vim-latexsuite
vim-addon-manager
vim-full
vim-common
vim-gnome
vim-gui-common
vim-doc

and yet, I get
```

pmckenne@adolpho:~$ vim --version
VIM - Vi IMproved 7.1 (2007 May 12, compiled Jan  8 2009 02:12:04)
Included patches: 1-314
Compiled by buildd@rothera.buildd
Small version without GUI.  Features included (+) or not (-):
-arabic -autocmd -balloon_eval -browse +builtin_terms -byte_offset -cindent 
-clientserver -clipboard -cmdline_compl +cmdline_hist -cmdline_info -comments 
-cryptv -cscope -cursorshape -dialog -diff -digraphs -dnd -ebcdic -emacs_tags 
-eval -ex_extra -extra_search -farsi -file_in_path -find_in_path -folding 
-footer +fork() -gettext -hangul_input +iconv -insert_expand +jumplist -keymap 
-langmap -libcall -linebreak -lispindent -listcmds -localmap -menu -mksession 
-modify_fname -mouse -mouse_dec -mouse_gpm -mouse_jsbterm -mouse_netterm 
-mouse_xterm +multi_byte -multi_lang -mzscheme -netbeans_intg -osfiletype 
-path_extra -perl -printer -profile -python -quickfix -reltime -rightleft -ruby
 -scrollbind -signs -smartindent -sniff -statusline -sun_workshop -syntax 
-tag_binary -tag_old_static -tag_any_white -tcl +terminfo -termresponse 
-textobjects -title -toolbar -user_commands -vertsplit -virtualedit +visual 
-visualextra -viminfo -vreplace +wildignore -wildmenu +windows +writebackup 
-X11 +xfontset -xim -xsmp -xterm_clipboard -xterm_save 
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
      user exrc file: "$HOME/.exrc"
  fall-back for $VIM: "/usr/share/vim"
Compilation: 
gcc -c -I. -Iproto -DHAVE_CONFIG_H     -g -O2 -O2 -g -Wall -DTINY_VIMRC        
Linking: gcc   -Wl,--as-needed -L/usr/local/lib -o vim    -lncurses  -lselinux 

```

I'm not new to linux, but vim and firefox are virtually the only things I ever use.  Is there something stupid I might be missing?

Thanks.

---

### Post by fishyboy on 2009-07-14
I have to say this problem is starting to annoy me now! I've flirted with some other text editors for a bit, but I keep coming back to my plain vim. I really want to get the colours back again!

I've done a bit more investigation, and I've finally made some progress. I haven't fixed the problem yet, but I think it's to do with vim not knowing the location of the syntax files. Here's what I've tried...

When I open a bash script (for example) in vim I haven't got any syntax highlighting. Trying to change the colour scheme doesn't work, which indicates a path config problem:

```
:colorscheme blue
--> E185: Cannot find colour scheme blue
```

But I can change the colour scheme by sourcing the full path of the colour scheme file. On my system this looks like...

```
:source /usr/share/vim/vim72/colors/blue.vim
```

After that everything looks a disgusting blue colour (does anyone really use that colour scheme?) Anyway, despite the blueness, there is still no syntax highlighting. But I can get it by sourcing the syntax file, in the case sh.vim.

```
:source /usr/share/vim/vim72/syntax/sh.vim
```

I've now got syntax highlighting back!

The next step is to figure out how to get vim to do this automatically...

Cheers.

---

### Post by kogger on 2009-07-14
Put "source /usr/share/vim/vim72/syntax/sh.vim" into your vimrc file, which can be either /usr/share/vim/vimrc or ~/.vimrc

---

### Post by fishyboy on 2009-07-14
Hi,

I've tried adding the "source..." parts to my .vimrc, but it doesn't make any difference. In any case, I don't always want to use the sh.vim highlighting - it won't make my Python scripts look very nice! And the syntax highlighting used to work before using my current .vimrc, so I think the problem is elsewhere. It could well be that I need to add the "source..." to another file. Hopefully though, I'll just need to update a path or environment variable.

Somewhere vim must decide the type of file being edited, and then source the appropriate syntax file. Or something like that. I'm not exactly sure how it all fits together, but I'm getting closer.

Cheers.

---

### Post by fishyboy on 2009-08-03
> **fishyboy said:**
> Hello all,

A few weeks ago I upgraded to Ubuntu 9.04, and ever since Vim does not highlight source code. I've tried obvious things like ":syn on", and I've also removed and reinstalled all vim-related things using aptitude. But I'm still stuck with one colour. Oh yes, I'm talking about the terminal version of Vim, although I've just tried GVim and that also has no syntax highlighting.

Does anyone know how I can restore Vim's syntax highlighting?

Cheers.

It took a while, but I've fixed it now. The problem was with my ~/.vimrc file, which contained a line setting the run-time path for vim. It looked like this (but all on one line)...

```
set runtimepath=~/.vim,/var/lib/vim/addons,
/usr/share/vim/vimfiles,
/usr/share/vim/vim71,
/usr/share/vim/vimfiles/after,
/var/lib/vim/addons/after
```

The vim I have is version 7.2. I just deleted the above line from my ~/.vimrc file and everything is back to normal. :D

---

### Post by Neovos on 2011-05-24
> **fishyboy said:**
> It took a while, but I've fixed it now. The problem was with my ~/.vimrc file, which contained a line setting the run-time path for vim. It looked like this (but all on one line)...

```
set runtimepath=~/.vim,/var/lib/vim/addons,
/usr/share/vim/vimfiles,
/usr/share/vim/vim71,
/usr/share/vim/vimfiles/after,
/var/lib/vim/addons/after
```

The vim I have is version 7.2. I just deleted the above line from my ~/.vimrc file and everything is back to normal. :D

Thanks very much for this. I had the same problem with updating to Natty except my path was /vim72 and changing it to /vim73 fixed my highlighting. 

I suspect it could be a bug in fact with upgrading vs. installing fresh. Upgrading a system might keep that folder name the same but update the contents where installing fresh (which is what I did for Natty via the alternate CD install) names that folder with the correct version. In either case, I would think a vim installer should check any existing .vimrc for these version specific filenames if it knows it will be changing them? Who knows.

---

### Post by mechsin on 2011-05-30
I had the same problem but I found is was because while the vim72 folder in /usr/share/vim was there it was almost empty. The best I can figure is that Ubuntu was getting confused and some how associating my vimrc with the partial vim72 and wasn't sourcing it when it ran vim73. So my solution was to just remove the vim72 file all together after that it on starting gvim it sourced my vimrc just fine. 

For reference my vimrc is located at $HOME/.vimrc

---

