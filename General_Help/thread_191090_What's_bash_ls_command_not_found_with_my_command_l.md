---
title: "What's bash: ls: command not found with my command line?"
date: 2006-06-07
forum: General Help
---

### Post by Hoffmann on 2006-06-07
Sundenly, I "lost" my commands. For example, if I type:
>  ls

I get:
>  bash: ls: command not found 

What's happened? How could I fix this?
Thanks!
:confused:

---

### Post by caldevil on 2006-06-07
what is the output of "echo $PATH"

---

### Post by Hoffmann on 2006-06-07
[QUOTE=caldevil]what is the output of "echo $PATH"[/QUOTE]

It is:

>  /usr/local/psa/bin:$PATH:/home/hoffmann/bin

---

### Post by caldevil on 2006-06-07
you have messed up with the PATH variable. You need to fix it. Is the problem there even if you reboot the computer?

---

### Post by Hoffmann on 2006-06-07
[QUOTE=caldevil]you have messed up with the PATH variable. You need to fix it. Is the problem there even if you reboot the computer?[/QUOTE]
I already solved the problem. I made a mistake on my .bashrc file. All is fine now.
Thanks :-D

---

