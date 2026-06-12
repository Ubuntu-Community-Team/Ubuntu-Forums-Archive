---
title: "Default/System ~ home directory"
date: 2010-02-10
forum: General Help
---

### Post by mttza1 on 2010-02-10
How can the default home directory, used by bash's adduser command, when the --home argument is not used, be changed?

For example, without changing the default, creating the user "bob", would assign him ~ = /home/bob, but having changed the default from home to NEW, he is assigned ~ = /NEW/bob.

there was a previous thread about this [here]("http://ubuntuforums.org/showthread.php?t=1338595&highlight=Default%2FSystem+home+directory"), (posted in 2007) however it was never answered.

thanks in advance

After looking at the useradd file in /etc/defaults, I found a comment saying that the HOME= thing in user add is the same as the DHOME (Default Home) in adduser. where is the adduser config gile, as it is not in /etc/defaults ?

---

### Post by mttza1 on 2010-02-10
The adduser.conf file is in /etc/ and the useradd.conf file is in /etc/defaults

edit DHOME in adduser.conf, and HOME in useradd.conf

Im not sure how to edit "users and groups" config at this point.

doing this only seems to affect the adduser command, not the useradd (I don't get why) or the Users and Groups program (maybe it uses useradd - or maybe its own code?).

---

### Post by mttza1 on 2010-11-09
*bump*

---

