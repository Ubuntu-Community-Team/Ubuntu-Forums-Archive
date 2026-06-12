---
title: "Auto-run a script on login - ./~bashrc not working"
date: 2011-10-18
forum: General Help
---

### Post by Gias Kay on 2011-10-18
Hello everyone,

On my Natty server I got a Bash Script I'd like to auto-run on login; I googled and read some solution about putting this setting inside ./~bashrc:

```
bash *my_script*
```

But this only made the script to auto-run whenever a terminal was opened and not exactly what I was looking for. So I am hoping if anyone could tell me the right way to do it. 

The script generates output if manually run inside the terminal, but I'd like that to be suppressed if it's auto-run (actually I'm not sure where the output will go if it's auto-run). Thank you very much!

---

### Post by dFlyer on 2011-10-18
My guess is to search for startup programs and enter you script in there. Putting anything in bash will only run when you start a terminal.

---

### Post by Atamisk on 2011-10-18
THe solution to this issue is largely dependant on HOW you're logging in. So, how are you logging in? I notice you said server, so i'm not assuming anything at this juncture!

---

### Post by Gias Kay on 2011-10-18
> **Atamisk said:**
> THe solution to this issue is largely dependant on HOW you're logging in. So, how are you logging in? I notice you said server, so i'm not assuming anything at this juncture!

It's Natty Server edition, logging in through password-disabled SSH (require PGP Key instead).

---

### Post by Gias Kay on 2011-10-18
> **dFlyer said:**
> My guess is to search for startup programs and enter you script in there. Putting anything in bash will only run when you start a terminal.

Does this means I should make it sh instead?

---

### Post by Atamisk on 2011-10-18
doesn't ssh drop into a bash shell when you log in? if so, i would've thought it'd run .bashrc when you logged in... either way, if it *is* bash when you log in, i've never encountered a bash that didn't run ~/.bash_aliases upon login. That's a messy fix, i know, so hopefully somebody has a better informed idea!

Cheers, 
-Aaron

---

