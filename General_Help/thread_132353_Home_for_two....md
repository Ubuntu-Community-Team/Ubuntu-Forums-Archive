---
title: "Home for two..."
date: 2006-02-18
forum: General Help
---

### Post by Haegin on 2006-02-18
Hi,
I have just installed fedora FC4 alongside ubuntu to try it out and to gain experiance with a non debian based distro. When I booted into fedora it wouldn't let me login to X but I could login through the console. I found the problem was permissions on the home directory and to login I had to "chown -R harry /home/harry". I did this and I can now login to fedora fine but now I cannot login to ubuntu.

To complicate matters even more my graphics card is dodgy (I think its partly broken) and I cannot enter a virtual term (ctrl + alt + number), restart x (ctrl + alt + backspace) or shutdown/restart/logout (all rather annoying). Fedora works fine as I have not updated the drivers but it does mean that in ubuntu I cannot drop into a terminal to chown home. Also I don't particularly want to have to keep chowning everytime I boot the other distro. Is it possible to let my user login to both and share the house?

My username is harry on both and both passwords are the same.

---

### Post by Haegin on 2006-02-19
any clues?

---

### Post by Haegin on 2006-02-20
nothing?

---

### Post by pt78 on 2006-02-20
Does not solve the probelm, but what about running chown as part of startup scripts (in both systems)?

---

### Post by schilcha on 2006-02-20
Check the UIDs of both of your harrys. ```
grep harry /etc/passwd
```
You'll get something like 
> 
harry:x:UID:GID:Harrys full name,,,:/home/harry:/bin/bash

where UID and GID are numbers. At least UID should match between ubuntu and fc4.

Good Luck!

---

