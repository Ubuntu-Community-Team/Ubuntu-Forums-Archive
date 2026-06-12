---
title: "New useradd not found"
date: 2010-12-21
forum: General Help
---

### Post by simsym05 on 2010-12-21
Morning,

i created a new user, this what i did with root account:
#useradd lisa
#passwd lisa
and i set a passwd
then when i go /home:
/home#ls
samy
i find only my user name;  there is no lisa account, i restarted my computer and lisa account already exist except it is not possible to login
so i log again as root
and i checked again to login as lisa account but the problem is the same, i have the notification:
root@ubuntu:/home# cd lisa
bash: cd: lisa: Aucun fichier ou dossier de ce type =>: that means  => 
bash: cd: lisa: no file or directory type exist

Can you help me please, to explain what is the problem and how to resolve it?
Thanks in advance.
Samy

---

### Post by simsym05 on 2010-12-21
Another question please, regarding creating new user account 

is this deffault useradd is correct:
root@ubuntu:/home# useradd -D
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
**[COLOR=Red]SHELL=/bin/sh[/COLOR]**
SKEL=/etc/skel
CREATE_MAIL_SPOOL=no


usaually i see **[COLOR=Red]SHELL=/bin/bash[/COLOR]**

Thanks

---

### Post by Dave_L on 2010-12-21
As a start, look at the file /etc/passwd, and compare the lines in that file for your old user and the new user.

---

### Post by simsym05 on 2010-12-21
Morning Dave

Account lisa exist, this what i have:
#cat /etc/passwd
.....
...
[COLOR=Red]lisa:x:1001:1001::/home/lisa:/bin/sh[/COLOR]

---

### Post by karthick87 on 2010-12-21
[INDENT]```
sudo useradd -d /home/username -m username
```
 ```
sudo passwd username
```
 The -d option is to set the home directory for the user.The -m option will force useradd to create the home directory.
 [/INDENT]

---

### Post by george21 on 2010-12-21
> **simsym05 said:**
> Morning Dave

Account lisa exist, this what i have:
#cat /etc/passwd
.....
...
[COLOR=Red]lisa:x:1001:1001::/home/lisa:/bin/sh[/COLOR]

In Ubuntu Linux no [duplicate files]("http://www.ashisoft.com") are created its very good operating system to be used on personal computers and Thanks!

---

### Post by simsym05 on 2010-12-21
> **karthick87 said:**
> [INDENT]```
sudo useradd -d /home/username -m username
``` ```
sudo passwd username
``` The -d option is to set the home directory for the user.The -m option will force useradd to create the home directory.
 [/INDENT]

Thank you very much for your help :)
The account is created and i have access too, but i don't understand what is the problem exactly, can you explain to me please.

Regarding the command i used it without sudo because i'm in root account, that will be the same if im inside another account without root access?

---

### Post by efflandt on 2010-12-21
You should really be using **adduser** instead of **useradd**.  If you read **man useradd** it says:

> useradd is a low level utility for adding users. On Debian, administrators should usually use adduser(8 ) instead.Ubuntu is a Debian based system.

---

### Post by simsym05 on 2010-12-21
> **efflandt said:**
> You should really be using **adduser** instead of **useradd**.  If you read **man useradd** it says:

Ubuntu is a Debian based system.


Thank you for this info, i just tried this command and i had more options, that seems good
Thanks again

---

