---
title: "gnu screen interfering with emacs (i think)"
date: 2012-09-05
forum: General Help
---

### Post by InkyDinky on 2012-09-05
I'm running cygwin on windows at work. I'm editing code in emacs(-nox) under gnu screen.  Occasionally in my haste to enter commands I'll enter some keystroke that blanks the screen and prompts with "Key". I'll hit a key and then it'll prompt "Again"  this usually breaks my C-x C-s save sequence in emacs. The C-x registers in emacs but C-s won't be recognized.
The keystroke is C-[some character I'd type with my left hand] that brings up the key/again prompt.
I'm pretty sure this is screen interfering with emacs and not me screwing up the keybindings of emacs.

Am I redefining a keybinding for screen? Is there a key sequence such as Esc-Esc-Esc in emacs that exits you out of a command?

Also if I have an emacs instance open in another window prior to breaking emacs the other instance of emacs won't be broken. Yet if I close the window in screen and open a new one and then run emacs the C-x C-s sequence will be broken in that window and all subsequent windows opened. 
I can close and reopen emacs in the window open prior to breaking emacs and the C-x C-s sequence still works. 
Logging out of screen and restarting resolves the problem.

Thanks.

---

