---
title: "New user - Unable installing desktop on server"
date: 2009-07-07
forum: General Help
---

### Post by mbodifee on 2009-07-07
Hello there, 
I am a total beginner at Ubunto.
I installed Ubuntu server 9.04 via iso on a Virtual Machine.
 
Now I am trying to start gui via sudo apt-get ubuntu-desktop.
I get message: 
E: Invallid operation Ubuntu desktop.
 
E: is the letter assigned to drive for "iso".
 
any idea how to start gui?

---

### Post by amauk on 2009-07-07
you missed out "install" from the apt-get command
```
sudo apt-get install ubuntu-desktop
```

btw, E: just means error
(so you can search log files easily for any errors)

---

