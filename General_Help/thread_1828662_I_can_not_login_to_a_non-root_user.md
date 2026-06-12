---
title: "I can not login to a non-root user"
date: 2011-08-19
forum: General Help
---

### Post by lampa20 on 2011-08-19
Hello,

I was working in some program and saving files didnt work (to home folder). It said permission denied. So i set chmod 777 to my home folder /home/ondra and hell hapened. Almost all programs didnt work. Even I could not shutdown PC so i logged in as a root and set chmod 755 to home folder but that didnt helped :( Every time I want to login as non-root user it says: "Unable to cd /home/ondra".

I have no idea what should I do with it :( Help please! Sorry for bad english.

drwxr-xr-x 76 ondra ondra 4096 2011-08-19 12:37 /home/ondra/

---

### Post by sisco311 on 2011-08-19
[thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by lampa20 on 2011-08-19
> **sisco311 said:**
> [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

root@bt:~# chown ondra /home/ondra/.dmrc
chown: cannot access `/home/ondra/.dmrc': No such file or directory
root@bt:~#

---

