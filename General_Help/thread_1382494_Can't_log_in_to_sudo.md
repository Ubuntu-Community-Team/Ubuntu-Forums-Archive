---
title: "Can't log in to sudo"
date: 2010-01-16
forum: General Help
---

### Post by shifterdriver13 on 2010-01-16
Hey, I'm running xubuntu 8.04 and I can't log into sudo in terminal, it just comes up with several strings of values and doesn't ask for my password. How can I fix this?

---

### Post by pirateghost on 2010-01-16
> **shifterdriver13 said:**
> Hey, I'm running xubuntu 8.04 and I can't log into sudo in terminal, it just comes up with several strings of values and doesn't ask for my password. How can I fix this?

are you running a command along WITH sudo?  you cant just log in as sudo

---

### Post by sliketymo on 2010-01-16
code : man sudo

---

### Post by jocko on 2010-01-16
> **shifterdriver13 said:**
> Hey, I'm running xubuntu 8.04 and I can't log into sudo in terminal, it just comes up with several strings of values and doesn't ask for my password. How can I fix this?
What do you mean with "log in to sudo"?
sudo is not something you log in to in any way, you just put it in front of another command to run that command as root (or any other user).
So if you want to run the command "apt-get update" as root, just run:
```
sudo apt-get update
```If you want to get a root shell, just run any of these:
```
sudo su
sudo -i
```And type "exit" to exit the root shell and get back your normal user shell...


If you just run "sudo" without any options or without specifying which program you want to run, you'll just get information on how to use sudo.

---

