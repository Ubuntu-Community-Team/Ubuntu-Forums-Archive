---
title: "Ubuntu's Shell: Tab Completion"
date: 2011-03-15
forum: General Help
---

### Post by I Forgot My Username on 2011-03-15
I noticed Ubuntu's shell has much better tab completion than others. What does this come from? I'm trying to get the same for FreeBSD, and apparently it takes more than just Bash.

---

### Post by jerome1232 on 2011-03-16
This is just me hitting google because your question made me curious.

But it appears to be system specific and usually in .bashrc, if not in there .bashrc should source the file that the rules are setup in.

Looking my .bashrc I can see it looks in /etc/bash_completion for programable rules of tab completion, maybe that file (on an ubuntu system) will have your answers.

---

### Post by I Forgot My Username on 2011-03-17
I'll have to wait until I boot into FreeBSD again to compare the two. Seems promising, thanks.

---

