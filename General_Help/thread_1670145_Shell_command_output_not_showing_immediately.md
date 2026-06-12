---
title: "Shell command output not showing immediately"
date: 2011-01-18
forum: General Help
---

### Post by cloudRunner on 2011-01-18
This is an extremely weird issue that I can't find any help with on Google.  It is minor but extremely annoying.

When I type in a linux command in the terminal, (e.g. "ls -la"), and then press enter, the cursor goes to the next line and just sits there, as if its processing some long command.

If I press enter again, I see the ls output as well as my prompt twice.  It's like the terminal window isn't auto-scrolling, but I've also seen this happen when there wasnt even enough text in the console screen to warrant a scrollbar.  Has anyone seen this before and know what I need to do?  I hope what I'm asking about makes sense.

I'm running 10.10 Gnome inside VMware Player, if that makes a difference.

---

### Post by cloudRunner on 2011-01-19
bump

---

### Post by dracayr on 2011-01-19
so this is either a problem with bash or with your terminal simulator (probably the latter). To find out, check what it does in a tty (press Ctrl+alt+F1, login and try a command).
If it's the terminal, installing a different terminal might help. I use terminator (sudo apt-get install terminator). Additionally to the normal terminal features, terminator can split the window horizentally or vertically into two (or more) shells. It's very useful :)

---

### Post by dracayr on 2011-01-19
so this is either a problem with bash or with your terminal simulator (probably the latter). To find out, check what it does in a tty (press Ctrl+alt+F1, login and try a command).
If it's the terminal, installing a different terminal might help. I use terminator (sudo apt-get install terminator). Additionally to the normal terminal features, terminator can split the window horizentally or vertically into two (or more) shells. It's very useful :)

---

