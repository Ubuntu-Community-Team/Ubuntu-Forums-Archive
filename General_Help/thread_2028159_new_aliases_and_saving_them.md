---
title: "new aliases and saving them"
date: 2012-07-17
forum: General Help
---

### Post by ZenMasta on 2012-07-17
I want to add some new aliases but if I simply type alias mystuff it will only work for the session

I tried to edit .bashrc but it seems they still do not work.

After editing that file if I try to /.bashrc it says 
bash: /.bashrc: No such file or directory

even with root.

---

### Post by Vaphell on 2012-07-17
/ as in root directory? .bashrc is in ~ (~/.bashrc)

besides if you modified that file your new instances of terminal should have those aliases enabled. Have you tried opening new terminal window?

---

### Post by Cheesehead on 2012-07-17
> **ZenMasta said:**
> After editing that file if I try to /.bashrc it says 
bash: /.bashrc: No such file or directory

even with root.

It's just a typo away:
/.bashrc is in the root directory, and not used by any user.
~/.bashrc reloads the user's file.

---

### Post by efflandt on 2012-07-17
There is no /.bashrc (in "/" directory).

~/.bashrc or $HOME/.bashrc is your personal one or /etc/bash.bashrc is the global one.

But if you properly add an alias to your personal .bashrc I don't even think you need to run ~/.bashrc, since I think that is sourced whenever a bash command is run.  Or maybe because I closed that terminal and opened another terminal (which likely sources .profile which sources .bashrc), an alias I added simply worked.

Whatever the case, I did not need to log out of X and back in for the alias to take effect.  If an added alias does not work in your current terminal, just open another xterm.

---

