---
title: "root troubles"
date: 2010-04-11
forum: General Help
---

### Post by kornell on 2010-04-11
hi my beloved,

i've installed a xeroxphaser 3100 multifunction printer. Drivers available are only for ubuntu 7.1. I have 9.1. the printer works correctly (more or less). The scanner works only under root. I found on an italian forum this solution

sudo adduser $user lp
sudo adduser $user lpadmin

than restart session

what i receive back is:

silver@silver:~$ sudo adduser $silver lp
adduser: L'utente «lp» esiste già. (user already exists)
silver@silver:~$ sudo adduser $silver lpadmin
adduser: Il gruppo «lpadmin» esiste già. (group already exists)
silver@silver:~$ 

anyone can help?

---

### Post by undecim on 2010-04-11
I think the commands you want are
```
sudo gpasswd -a silver lp
sudo gpasswd -a silver lpadmin
```
to add yourself to the lp and lpadmin groups

---

### Post by kornell on 2010-04-11
you already know i love u

thanks

---

