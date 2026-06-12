---
title: "prevent use of Ctrl+C in .bashrc"
date: 2012-01-16
forum: General Help
---

### Post by compiz addict on 2012-01-16
I like having a password protected terminal on my computer using .bashrc, but the ability to use Ctrl+C to terminate .bashrc makes that idea quite useless. Any solution to that?

Also, the password system uses an if statement that has the password written in plain text in it. Any better method for that?

---

### Post by compiz addict on 2012-01-16
*bump*

---

### Post by Serpher on 2012-01-16
[http://www.cyberciti.biz/faq/unix-linux-shell-scripting-disable-controlc/](http://www.cyberciti.biz/faq/unix-linux-shell-scripting-disable-controlc/)

More results can be found with a simple Google search. What's the point of this though? You already need a password to login or do anything you couldn't do in the GUI if you're not using a CLI.

---

### Post by compiz addict on 2012-01-16
It's just additional security for my SSH server. My script not only asks for a password but also a session name; there are a few accepted session names that my friends use and choosing different session names logs the current time that session name was used and depending on what I want that person being able to do puts aliases over dangerous commands.

More so just because I can than anything else! :D

---

