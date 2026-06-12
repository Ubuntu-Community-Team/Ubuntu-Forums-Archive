---
title: "I am having trouble updating with Update Manager"
date: 2009-07-13
forum: General Help
---

### Post by castlefox on 2009-07-13
I am using Ubuntu 8.10 

After I use Update Manager it finds thing that it can update like usual but then an error occurs and it says:

 "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."


I tried putting dpkg --configure -a into Terminal, it tell me:

"dpkg: requested operation requires superuser privilege"


I dont know how I 'log in' or whatever through terminal.  

If anyone can help me, big thanks

---

### Post by carml on 2009-07-13
Just write sudo before tht command and you'll get the job done. 
For the future remember that some actions require the command sudo to be performed,with sudo the user (you or someone else,if there's more than one user) can perform an action as administrator. :)

---

### Post by castlefox on 2009-07-13
oh wow, you unlocked the Ubuntu secrets for me

Thank you carml

---

