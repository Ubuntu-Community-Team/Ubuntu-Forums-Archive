---
title: "Vim Arrow Keys Not Working"
date: 2011-11-01
forum: General Help
---

### Post by theburningor on 2011-11-01
In insert mode, my arrow keys are showing A B C D instead of actually moving around.  This isn't generally a big deal for me as I am pretty hardcore about using vim-style keybindings.  However, it makes using any sort of menu plugin (FuzzyFinder, Snipmate, OmniTab) basically impossible since moving up and down in those menus gets interpreted as a letter, rather than allowing me to select what I want.

I've been searching around for a while and all the solutions I've found don't seem to apply to me.  

 - I have "set nocompatible"  set in my ~/.vimrc file (Necessary for all my plugins)
 - I am running Vim 7.3 and it is vim-tiny is not installed

I'm not sure if this started exactly when I upgraded to Oneiric because I hadn't been using this Ubuntu machine for several months but I know for sure that they were working fine last spring.

Any thoughts?

---

### Post by haqking on 2011-11-01
> **theburningor said:**
> In insert mode, my arrow keys are showing A B C D instead of actually moving around.  This isn't generally a big deal for me as I am pretty hardcore about using vim-style keybindings.  However, it makes using any sort of menu plugin (FuzzyFinder, Snipmate, OmniTab) basically impossible since moving up and down in those menus gets interpreted as a letter, rather than allowing me to select what I want.

I've been searching around for a while and all the solutions I've found don't seem to apply to me.  

 - I have "set nocompatible"  set in my ~/.vimrc file (Necessary for all my plugins)
 - I am running Vim 7.3 and it is vim-tiny is not installed

I'm not sure if this started exactly when I upgraded to Oneiric because I hadn't been using this Ubuntu machine for several months but I know for sure that they were working fine last spring.

Any thoughts?

[http://vim.wikia.com/wiki/Fix_arrow_keys_that_display_A_B_C_D_on_remote_shell](http://vim.wikia.com/wiki/Fix_arrow_keys_that_display_A_B_C_D_on_remote_shell)

---

### Post by theburningor on 2011-11-01
I've spent a good deal of time on that page.  I should have mentioned that, from that page, I've found that setting "set term=builtin_ansi" will get it to work, but that breaks my syntax highlighting (which is more important to me than the arrow keys).

---

### Post by haqking on 2011-11-01
> **theburningor said:**
> I've spent a good deal of time on that page.  I should have mentioned that, from that page, I've found that setting "set term=builtin_ansi" will get it to work, but that breaks my syntax highlighting (which is more important to me than the arrow keys).

not sure other than what i already knew.

All i can do is the same as you which is google.

[http://stackoverflow.com/questions/4303830/vim-problem-with-arrow-keys-in-insert-mode-in-mac-terminal-app](http://stackoverflow.com/questions/4303830/vim-problem-with-arrow-keys-in-insert-mode-in-mac-terminal-app)

This provides some solutions, though it is for mac but i doubt that matters

and here [http://groups.google.com/group/vim_use/browse_thread/thread/61f8fd9c50b22588](http://groups.google.com/group/vim_use/browse_thread/thread/61f8fd9c50b22588)

seems to be a plugin which causes the issue

---

### Post by theburningor on 2011-11-01
That Google thread seems like a decent start.  I know autoclose creates this issue, but I don't use that extension.

---

### Post by haqking on 2011-11-01
> **theburningor said:**
> That Google thread seems like a decent start.  I know autoclose creates this issue, but I don't use that extension.

well sorry i cant be of more help, perhaps someone else will chime in with a solution.

If you find one, post it back.

Cheers

---

### Post by theburningor on 2011-11-01
I'll definitely post on here if I find any solutions.  Does seem to be only a terminal issues.  Doesn't happen in Gvim.

---

