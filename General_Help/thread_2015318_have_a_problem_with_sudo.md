---
title: "have a problem with sudo"
date: 2012-07-03
forum: General Help
---

### Post by amertarekt on 2012-07-03
i have ubuntu 12.04 final version 

when i am trying to make any sudo command 

for example sudo apt-get update i get this error

```

sudo: unable to open /etc/sudoers: Permission denied
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

```

i tried to edit sudoers file using recovery mode and visudo using nano editor but it said the sudoers file is read only file 

so what can i do now and please give me steps


**will upgrading ubuntu 12.04 to ubuntu 12.10 solve this problem or i must to install a fresh setup? **

---

### Post by Rodney9 on 2012-07-03
This should help -

[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Rodney

---

### Post by Lars Noodén on 2012-07-03
If that doesn't fix it, check to see that your account is a member of the group 'sudo'.

---

### Post by amertarekt on 2012-07-03
> **Lars Noodén said:**
> If that doesn't fix it, check to see that your account is a member of the group 'sudo'.

it does not work for me 

how can i know my user member of group sudo?

when i tried to add my user as admin it said to me that it already added

---

### Post by Lars Noodén on 2012-07-03
You can see which groups your account is a member of with the program [groups](http://manpages.ubuntu.com/manpages/precise/en/man1/groups.1.html).

---

