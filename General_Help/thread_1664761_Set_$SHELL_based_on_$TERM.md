---
title: "Set $SHELL based on $TERM"
date: 2011-01-11
forum: General Help
---

### Post by dglmoore on 2011-01-11
I use several different terminal emulators based on what I am working on. With each of these terminals I have a preferred shell. For example, I like bash in xterm and rc in 9term. I don't want to execute 
```
9term rc
```
every time I run 9term.

How can I, using .profile, .bashrc, .bash_profile, etc. to set the shell to be used by each terminal based on the $TERM variable?

I would prefer to not use aliases for reasons that are not relevant.

My default shell is bash. And have tried several things so far. Any help would be nice.

---

### Post by papibe on 2011-01-13
Maybe creating a launcher/shortcut in the menu (or better on the top panel) could be a simple solution. On the launcher's properties you can choose what program to run and its arguments. 

You could create as many launchers as you need: one for 9term, other for 9term rc, another for xterm, etc.

I hope it helps.

---

