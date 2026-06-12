---
title: "trouble with .bashrc on fresh reinstall?"
date: 2010-04-01
forum: General Help
---

### Post by adpads on 2010-04-01
Hi all -

I am running a fresh reinstall of Ubuntu Karmic, which is reading its settings from an old /home partition. Tinkering away and getting it smoothed out. Pretty much everything is running smoothly, except for one thing:

When I open a terminal, my prompt does not show $PS1, and it does not appear to be executing the contents of .bashrc. I have tried several different .bashrc files, and logging in as different users, with the same results: the terminal prompt is a mere, laconic $, with nothing behind it. Most annoyingly, the arrow keys do not take me back through the history, but instead write up on the screen ^[[A, ^[[B, and so on.

When I issue the su command, $PS1 displays just fine, and I can scroll back through history with the arrow keys. But copying the .bashrc file from /root into my user directory and setting the privileges to 777 does not fix the problem.

Regardless of what .bashrc is present, the command "source ~/.bashrc" gives the error "/bin/sh: source: not found". However, with root this works just fine.

What is my system missing?

Thank you all!

---

### Post by sisco311 on 2010-04-01
Sounds like bash is not your default login shell.

```
ps $$
```

To change your default login shell to bash, run:
```
chsh -s /bin/bash
```

EDIT:
> **adpads said:**
> 

Regardless of what .bashrc is present, the command "source ~/.bashrc" gives the error "/bin/sh: source: not found". However, with root this works just fine.



Yep, you are using /bin/sh...

---

### Post by adpads on 2010-04-01
Thanks for your quick answer!

I tried ps $$, and indeed it looks like my shell is /bin/sh:

> $ ps $$
  PID TTY      STAT   TIME COMMAND
16171 pts/2    Ss     0:00 /bin/sh


so I told it chsh -s /bin/bash, supplied my password, got no error messages or feedback - and nothing changed. I am still getting the same error message for source ~/.bashrc:

> /bin/sh: source: not found

we're on the right track though - is there some package I should uninstall to just get rid of /bin/sh?

thanks again!

---

### Post by sisco311 on 2010-04-01
> **adpads said:**
> Thanks for your quick answer!

I tried ps $$, and indeed it looks like my shell is /bin/sh:



so I told it chsh -s /bin/bash, supplied my password, got no error messages or feedback - and nothing changed. I am still getting the same error message for source ~/.bashrc:



we're on the right track though - is there some package I should uninstall to just get rid of /bin/sh?

thanks again!

You have to start a new shell/terminal (log out from your current shell & log back in).

Don't get rid of sh, many start-up scripts use it. Removing it will broke your system!

---

### Post by adpads on 2010-04-01
Yep, got it - restarted the system and the changes took effect. Working beautifully now.
And even more impressive, your reply was so fast, it was there in less time than it took Ubuntu to reboot!
Thanks again for your help!

---

### Post by sisco311 on 2010-04-01
> **adpads said:**
> Yep, got it - restarted the system and the changes took effect. Working beautifully now.
And even more impressive, your reply was so fast, it was there in less time than it took Ubuntu to reboot!
Thanks again for your help!

You're welcome!

---

