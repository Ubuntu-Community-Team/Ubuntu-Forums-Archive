---
title: "Unable to sudo or authenticate after passwd -d"
date: 2010-05-01
forum: General Help
---

### Post by dstojek on 2010-05-01
While installing Ubuntu I've set my user password which started to annoy me while doing sudo or something. I've decided to remove password with passwd -d user. After that I'm no longer able to use sudo. It asks for a password which I've removed.



```
damian@damian-laptop:~$ sudo su
[sudo] password for damian: 
Sorry, try again.
[sudo] password for damian: 
Sorry, try again.
[sudo] password for damian: 
Sorry, try again.
sudo: 3 incorrect password attempts
damian@damian-laptop:~$ 

```

//solved. I've forgot about simpliest passwd user :|

---

### Post by tie82 on 2013-04-01
I've got the same problem.

I deleted the password with 
sudo passwd -d username

And afterwards every su-commands asks for an password. Neither the old nor an empty password is working.

What can I do?

Thanks
tie


okay I solved it:
when executing "passwd" without sudo I was not asked for the old password. So I gave me a new one and afterwards I disabled the password in the system settings

---

### Post by wildmanne39 on 2013-04-01
Thread closed. Please do not post in old threads.

---

