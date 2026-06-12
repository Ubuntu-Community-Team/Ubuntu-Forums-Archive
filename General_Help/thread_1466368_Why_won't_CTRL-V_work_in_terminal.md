---
title: "Why won't CTRL-V work in terminal"
date: 2010-04-30
forum: General Help
---

### Post by Stolea on 2010-04-30
For some reason since 9.10 CTRL-V doesn't seem to work in my terminal. Used to work just fine, but now I have to Rightclick Paste any commands.
I cut my teeth on commandline inputs and this is a bit like having a dog and doing the barking myself:)

---

### Post by happyhamster on 2010-04-30
In a terminal you can use:

shift + ctrl + c = copy
shift + ctrl + v = paste

or : highlight whatever has to be copied, and paste by clicking middle-mouse button (this doesn't use the same 'clipboard' as (shift) ctrl + c however).

---

### Post by bdarb on 2010-04-30
you can also just change the key bindings in the terminal
Edit -> Keyboard Shortcuts
and manually change it there

---

### Post by efflandt on 2010-04-30
The shell and shell programs were developed way before X or MS Windows, so they may be using certain key combinations for other things.  The people familiar with those programs may become lost if key combinations do not do their ancient intended functions.

I was not aware of the shift key modifier for these functions, but it is easy enough to use the mouse buttons or Edit menu to copy and paste in a terminal program.

---

### Post by Stolea on 2010-04-30
Thanks for that. I am so used to keyboard commands that I can do things much faster that way. Old habits and all that gaff.
Cheers

Addendum:
Shift-Ctrl-C and Shift-Ctrl-V only work in the terminal. If you want to copy a command off a website and past it into a terminal you have to Ctrl-C on the website and Shift-Ctrl-V in the terminal.
Correspondingly Ctrl-C will terminate whatever you are doing on a terminal and Shift-Ctrl-V won't paste anything into a document.

---

