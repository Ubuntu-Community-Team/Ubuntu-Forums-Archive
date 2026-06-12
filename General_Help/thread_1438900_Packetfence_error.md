---
title: "Packetfence error"
date: 2010-03-25
forum: General Help
---

### Post by danhotrod on 2010-03-25
[SIZE=2]Hello,

I am having problems running packetfence on Ubuntu Desktop 9.10, when i try to start it this error message appears in the log:
Mar 24 17:47:52 pfcmd(0) FATAL: person user id 1 must exist - please reinitialize your database (main::sanity_check)

I've installed all the perl modules and nothing seems to be working.

Any ideas please? :)



[/SIZE]

---

### Post by gordintoronto on 2010-03-25
Did you reinitialize your database?

---

### Post by danhotrod on 2010-03-26
Thanks gordintoronto, but i don't know how to reinitialize a database :confused:

And just asking, which database is it and how do i reinitialize it?

Sorry to be such a newbie!

Thanks :)

---

### Post by gordintoronto on 2010-03-26
I would expect that information to be in the packetfence docs. Perhaps there is some configuration you need to do before you run it?  Linux is big on appname.conf files which are maintained by using a text editor in too many cases.

---

### Post by danhotrod on 2010-03-28
I have edited the pfcmd file and added !! to the lines in question.

That seemed to do something because the message about person user id disappeared

I am now having a error about something to do with HTTPD not existing!

I have checked the config files and the documentation and nothing seems to be
relevant to the error!

Can anyone shed some light on this?

---

