---
title: "Root user password?"
date: 2011-05-05
forum: General Help
---

### Post by mattintc10 on 2011-05-05
Iv looked through alot of old old threads and i got xubuntu 11.04. Apparently no one had stated the fact that i had to be root user to install ndiswrapper and what not. But now i can not figure how to get around it and get into the root user.

---

### Post by miasmablk on 2011-05-05
sudo -i

---

### Post by jerome1232 on 2011-05-05
Expanding on that a little bit.

So in Ubuntu the root account is locked, instead we use sudo to elevate admin accounts temporarily to do things as root (or another user)

You use the command sudo and use your accounts password.

ie

sudo command

or 

sudo -i
command
command
command
another command
exit

more about this sudo stuff here
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

