---
title: "One thing i have noticed"
date: 2009-11-05
forum: General Help
---

### Post by geoffmcc on 2009-11-05
I am currently running Ubuntu Server 9.10 and I usually just use putty from windows to ssh into it.

I find that when I have "had a few" it is a lot harder to do what i want to do from the shell. Maybe as time goes on i will get better at it but in the mean time im getting sick of retyping commands. Is there a close enough setting for terminal (lol)

---

### Post by soapBAR2 on 2009-11-05
Yep, aliases and tab-complete. To add an alias per session, type 

alias shortcut='command'

Which means that if you type "shortcut", you'll execute "command". However, you'll lose the information when you close the terminal. To make it persistent, put the same alias command in ~/.bashrc (if you use the default shell as bash - otherwise, put it in your shell-of-choice's RC).

"Tab complete" completes your command when you type the first bit and hit "tab". Have a play with it.

---

### Post by P4man on 2009-11-05
ubuntu server comes with a built-in alcohol lock. If you are too drunk to safely operate the machine it will pretend it doesnt know the commands you are typing ;)

But yeah, you can fool it with the above poster's advice. tab completion absolutely rocks, it also works for folder and file names (and btw, it also work on windows)

---

### Post by nothingspecial on 2009-11-05
> **geoffmcc said:**
> 

I find that when I have "had a few" it is a lot harder to do what i want to do from the shell.  (lol)

It depends how much you have, see [[COLOR="Magenta"]xkcd ballmer peak[/COLOR]]("http://xkcd.com/323/") for a graphical representation.

+1 for aliases and tab completion.


Where can I install this alcohol-lock. I`m running 8.04 server and I can`t find it in the repos \\:D/

---

### Post by geoffmcc on 2009-11-05
> **nothingspecial said:**
> It depends how much you have, see [[COLOR="Magenta"]xkcd ballmer peak[/COLOR]]("http://xkcd.com/323/") for a graphical representation.

That is good

---

