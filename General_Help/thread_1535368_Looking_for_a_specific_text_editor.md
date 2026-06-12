---
title: "Looking for a specific text editor"
date: 2010-07-20
forum: General Help
---

### Post by lorderico on 2010-07-20
Hello,

You know how nano, vi, vim, etc... all use the entire screen when they are started?  I am wondering if it is possible to get a text editor (or modifying an existing one) that doesn't take the entire terminal.  The reason for this is that I to look at the output of a different command, then modify a different file while looking at the output.  I want to be able to do this very fast, and it would be great if there was some way I could this all in one shell instead of creating two terminals and resizing or flipping between them.  I realize the ideal solution would be a second monitor, but I can't get that right now.  Thanks for and ideas,

Eric

---

### Post by oldos2er on 2010-07-20
In nano, use Ctrl-Z to access the shell. I'm sure vi/vim has a similar command, but I don't know what it is. You could also switch to another tty, or use a program like screen.

---

### Post by nmaster on 2010-07-20
you can run a shell in emacs as well.  M-x shell.  have the two buffers display side-by-side with either C-x 2 (horizontal split) or C-x 3 (vertical split)

---

### Post by nmaster on 2010-07-27
this is kind of late, but i recently read about a program called terminator on Ars Technica.

this might be what you want: [http://arstechnica.com/open-source/news/2010/07/terminator-for-gnome-lets-users-split-terminal-windows.ars](http://arstechnica.com/open-source/news/2010/07/terminator-for-gnome-lets-users-split-terminal-windows.ars)

---

### Post by agnes on 2010-07-27
In vim, you can launch a shell command by going into command-mode (ESC) and typing
*:!cmd*
(where cmd = command); you get a look of the output, then pressing Enter gets you back in vim.

I like Terminator too, it will serve your task fast if you know the keybindings. GNUScreen is something like that but solely with keybindings and it has no vertical split yet (afaik, though there is a patch) - nice thing about it is, you can keep processes running if the terminal window itself is closed.

---

### Post by lorderico on 2010-07-27
Just tried Terminator, it looks really good.  Only thing annoys me is the tabs are HUGE.  I'm not sure if that is an artifact of gnome or the program.  Other than that, it looks like a great option because I still use my favorite text editor (which happens to be nano w/o a gui or gedit w/ a gui).

Eric

---

### Post by nmaster on 2010-07-28
if you're willing to get used to emacs, i just realized that you can run a full terminal emulator in a buffer is "M-x term" ("M-x" shell" run a dumb terminal)

---

