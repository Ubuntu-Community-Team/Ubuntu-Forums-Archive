---
title: "Log users that enters opensshd"
date: 2009-06-30
forum: General Help
---

### Post by warlord360 on 2009-06-30
Hello,

I was wondering when somebody trys to log into sshd i would want it to save the wrong passwords attempts, and everytime someone trys to login, it would be nice to display it to a irc channel but i'm sure that cannot be done, but anyways how do i log? it's for security reasons.

---

### Post by t4thfavor on 2009-06-30
/var/log$ cat auth.log |grep Failed |grep ssh > ssh.txt

as for posting into irc, I am sure there is an irc client that can post from a txt file

---

