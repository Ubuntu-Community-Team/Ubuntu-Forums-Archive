---
title: "Pressing HOME or END in Vi produces a H or F character?"
date: 2009-11-09
forum: General Help
---

### Post by Buttons840 on 2009-11-09
I just installed Ubuntu 9.10, and while using Vi during my initial configuration I noticed that often when pressing the HOME or the END key Vi will insert a capital H or F on a new line by itself.

I suspected the keyboard may be improperly configured, but HOME and END work properly in all other applications as far as I can tell.  Including: firefox, xchat, terminal, the keyboard preferences screen, gedit.

Not sure where to even start with this issue.  Please help.

Thanks.

UPDATE:  In the end it appears to have something to do with vim compatibility mode.  By running the command "set nocompatible" I was able to get the behaviour I expected.  I placed "set nocompatible" into the $HOME/.vimrc file and now vi/vim behaves as expected all the time without me having to run :set nocompatible every time I start.  Thanks to falconindy

UPDATE:  I remove my solved tag because I've still been having problems.  Specifically when I'm in insert mode (with nocompatible set) I cannot backspace up to the previous line.  When I reach column 1 and continue to hit backspace nothing happens, backspace will not erase the line feed and start erasing the line above as I would expect.

Again, I'll voice my frustration.  Every distro I've tried using vi has always behaved the same (including all previous ubuntu distros) but suddenly in 9.10 it just doesn't work.

Also note that when I say vi, I mean vim.  Vi is not installed, but vim is.  When I type vi, it opens vim.  See below for terminal output showing this behaviour and showing which version of vim I'm using.

---

### Post by falconindy on 2009-11-09
Install Vim. The old Vi is bad. Also old.

---

### Post by Buttons840 on 2009-11-09
I suppose if "don't use the default that comes with the Ubuntu distro, install something else instead" is the best I can get, that's what I'll have to do.  However, I would hope this is not up to Ubuntu standards.

Actually, this is Vim, and I hadn't realized it.  I started the program by running "vi" at the terminal.  However, "vi --version" reveals:

```
vi --version
VIM - Vi IMproved 7.2 (2008 Aug 9, compiled Sep 21 2009 11:19:52)
Included patches: 1-245
Compiled by buildd@crested.buildd
Small version without GUI.  Features included (+) or not (-):
-arabic -autocmd -balloon_eval -browse +builtin_terms -byte_offset -cindent 
-clientserver -clipboard -cmdline_compl +cmdline_hist -cmdline_info -comments 
-cryptv -cscope -cursorshape -dialog -diff -digraphs -dnd -ebcdic -emacs_tags 
-eval -ex_extra -extra_search -farsi -file_in_path -find_in_path -float 
-folding -footer +fork() -gettext -hangul_input +iconv -insert_expand +jumplist
 -keymap -langmap -libcall -linebreak -lispindent -listcmds -localmap -menu 
-mksession -modify_fname -mouse -mouse_dec -mouse_gpm -mouse_jsbterm 
-mouse_netterm -mouse_sysmouse -mouse_xterm +multi_byte -multi_lang -mzscheme 
-netbeans_intg -osfiletype -path_extra -perl -printer -profile -python 
-quickfix -reltime -rightleft -ruby -scrollbind -signs -smartindent -sniff 
-statusline -sun_workshop -syntax -tag_binary -tag_old_static -tag_any_white 
-tcl +terminfo -termresponse -textobjects -title -toolbar -user_commands 
-vertsplit -virtualedit +visual -visualextra -viminfo -vreplace +wildignore 
-wildmenu +windows +writebackup -X11 +xfontset -xim -xsmp -xterm_clipboard 
-xterm_save 
   system vimrc file: "$VIM/vimrc"
     user vimrc file: "$HOME/.vimrc"
      user exrc file: "$HOME/.exrc"
  fall-back for $VIM: "/usr/share/vim"
Compilation: 
gcc -c -I. -Iproto -DHAVE_CONFIG_H     -Wall -g -O2 -DTINY_VIMRC        
Linking: gcc   -Wl,--as-needed -o vim    -lm -lncurses  -lselinux 

```

Is it expected behavior for HOME and END to produce H and F in Vim when I start it using the "vi" command?  I assume it's in some kind of compatibility mode?

Also, if I attempt to run the command "vim" I get "vim: command no found" in return.

```
vim
The program 'vim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-gtk
 * vim-nox
Try: sudo apt-get install <selected package>
vim: command not found
```

This is a FRESH Ubuntu 9.10 install.  The only thing I've installed is ndiswrapper and configured it.

---

### Post by Buttons840 on 2009-11-09
I also notice that I cannot turn on scroll lock, caps lock, and num lock all at the same time.  Is this normal?

Also, the arrow keys do not work, but produce A B C and D characters.  Again, in upper case.

---

### Post by falconindy on 2009-11-09
You must be in vi compatible mode then. Try running ":set nocompatible" in Vim. If that helps, toss it into $HOME/.vimrc (make the file if you need to).

---

### Post by artaxerxes on 2009-11-09
If this is happening in Insert or replace mode then I think that this is normal. If it is happening in command mode then it is not.

Are you by any chance new to vi (or vim)?
Assuming that you are, here is some info I hope is useful.

vi is modal, by that I mean it operates in one of two modes.

Text entry and command. You get out of a text entry with the escape key.
You get into a text entry mode with one of the text entry commands like "a" or "i".

When in text entry (Insert or replace) mode you type text. You can't move around. When in command mode you can move the cursor, delete stuff, replace things, search, change case, etc etc.

This might not be what you were expecting and hence the confusion.

A brief vi intro would probably be useful and clearer than my ramblings.
I don't know of one off hand but a google search of vi tutorial will probably turn up something.

I hope this helps

==============
edit:

The this I was talking about was the behavior of the arrow, home and end keys.
I am not sure what you are getting at with respect to caps lock .

---

### Post by falconindy on 2009-11-09
In a bizzare twist of fate, I'm now afflicted by this same malady, after a full day of Vim behaving properly. It works independent of which terminal I'm using, but doesn't affect GVim.

Meh, I'll fix it tomorrow.

---

### Post by Buttons840 on 2009-11-09
It must have been something to do with that compatibility mode.  "set nocompatible" did the trick and placing it in $HOME/.vimrc did the trick.  It now behaves as I expect vi should.

Thanks.

---

### Post by falconindy on 2009-11-10
Cool. My issue was a bad interaction with "set term=ansi" option in .vimrc.

---

### Post by Buttons840 on 2009-12-20
I cannot backspace.  When I'm backspacing and hit column 1 I cannot go further.  I cannot erase line feeds.

---

### Post by dcstar on 2009-12-20
> **Buttons840 said:**
> I cannot backspace.  When I'm backspacing and hit column 1 I cannot go further.  I cannot erase line feeds.

I really don't know why anyone in the last 10 years would ever use vi (**V**irtually **I**mpossible to use), if you want an easier to use terminal editor for simple text then use **nano**.

---

### Post by Buttons840 on 2009-12-20
> **dcstar said:**
> I really don't know why anyone in the last 10 years would ever use vi (**V**irtually **I**mpossible to use), if you want an easier to use terminal editor for simple text then use **nano**.

There are lots of things more difficult than working with Vi.  Saying "I don't know" is better than "just use something else;" and saying nothing is better than "I don't know."

---

### Post by dcstar on 2009-12-20
> **Buttons840 said:**
> There are lots of things more difficult than working with Vi.  Saying "I don't know" is better than "just use something else;" and saying nothing is better than "I don't know."
vi has never been an editor designed to be used with the convenience of modern screen based editors (that is why a lot of the others exist).

vi's main power comes from the POSIX commands that you can use for finding/replacing strings, and since it was originally designed for use on text terminals (usually over slow connections, where you could use it in single-line mode and not have to wait for slow screen refreshes) it is far from a productive tool in the modern era.

I had to use vi since the late 1980's, you quickly learn of the limitations of it and not having all the convenient keys and features that work in other editors is one of them.

---

### Post by Buttons840 on 2009-12-20
I find vim* more convenient then using a mouse/GUI in many situations, and sometimes a GUI isn't available.  

I installed the full vim package, and it's working as I expected now.  I'm still wondering if it's possible to get the same behaviour (namely, the ability to backspace) with vim-tiny which comes with the distro.

If not, then I'd like to see a the full vim version come with the distro.  I know there's enough free space on the disk.

*Just to be clear I've been talking about vim for the entire thread.  As I posted earlier using "vi" really using vim-tiny.

---

