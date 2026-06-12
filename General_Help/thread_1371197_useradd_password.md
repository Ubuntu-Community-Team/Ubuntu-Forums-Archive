---
title: "useradd password"
date: 2010-01-03
forum: General Help
---

### Post by Wouter N on 2010-01-03
Hello,

I am trying to install mysql community server edition from source, following this guide: [http://dev.mysql.com/doc/refman/5.1/en/installing-source.html](http://dev.mysql.com/doc/refman/5.1/en/installing-source.html)
I have to make a new user mysql, and then execute some commands as that user. So i tried *su mysql*, but then it prompts for a password.
I just added the user with *useradd -g mysql mysql*, leaving the password blank. I found out that leaving the password blank, results in the account being disabled for use. After some googling, I found out that the paramter -p of usermod expects an encrypted password with *crypt*.
It seems crypt wasn't installed on my distro(9.04), so I used *apt-get* to install mcrypt, some sort of emulation of crypt?
Using *mcrypt <password> encrypted-password*, I encrypted a text file only containing my password.
Finaly, I set up a password for mysql issuing the following command:
*sudo usermod -p encrypted-password mysql*.
But now when I try to *su mysql*, entering the password, it says everytime it isn't correct...
Where did it go wrong?

Thanks in advance,

Wouter

---

### Post by rnerwein on 2010-01-03
hi
why you ain't use the original command: passwd username
just open a terminal and type:
# passwd mysql

enter your password
that's it
ciao

---

### Post by Wouter N on 2010-01-04
Thank you, that worked perfectly!
I was searching too far for it apparently...

---

