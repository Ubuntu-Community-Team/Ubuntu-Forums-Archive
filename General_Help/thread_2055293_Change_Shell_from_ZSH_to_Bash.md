---
title: "Change Shell from ZSH to Bash"
date: 2012-09-09
forum: General Help
---

### Post by flebber on 2012-09-09
Hi

I am on 12.04, and I have changed my dfault shell to ZSH. Since pythonbrew cannot cope with ZSH I am changing back for the minute.

Except I don't know how to revert it back to bash, how can I ?

---

### Post by spjackson on 2012-09-09
chsh is the command to change your default shell.

---

### Post by flebber on 2012-09-09
when I use chsh it says changed to bash but it is still zsh

```
sayth@sayth-TravelMate-5740G[~]
[18:00]:chsh
Password: 
Changing the login shell for sayth
Enter the new value, or press ENTER for the default
	Login Shell [/bin/bash]: 

sayth@sayth-TravelMate-5740G[~]
[18:00]:echo $SHELL
/bin/zsh

```

---

### Post by zombifier25 on 2012-09-09
Try logging out and log in and see if the changes are in place.

---

### Post by flebber on 2012-09-09
Thanks that did the trick

---

### Post by raja.genupula on 2012-09-09
please mark your thread as solved from thread tools . Thank you .

---

