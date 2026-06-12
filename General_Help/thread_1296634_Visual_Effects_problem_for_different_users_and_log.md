---
title: "Visual Effects problem for different users and login screen resolution problem"
date: 2009-10-20
forum: General Help
---

### Post by emigrant on 2009-10-20
hi,
i have 3 users (1 admin and 2 normal users) in my machine.
iv enabled visual effects for the admin account (my account), but if i try to enable visual effects to the other two it says cannot enable. (it was enabled in all the 3 accounts before a bad shutdown which just occured)


help please
(today only installed jaunty :) )

also,
how can i set the dislplay resolution for the login screen?
at the first couple of logins it used to have 1024*768 but now its been changed to 800*600.
this happened after a bad shutdown.

thanks in advance

edit:
also how can i set a common hardware setting (display resolution, visual effects etc...) for all the users.
if not for each new user i have to log in to that account and configure :(

thanks

---

### Post by emigrant on 2009-10-21
iv figured out, whats happening.
at a time, only one user can stay logged in with the 'visual effects' enabled. if another user has to enable 'visual effects' the former one has to log off.

any one has a clue how to solve the problem?
:(

thank you ;)

---

### Post by wojox on 2009-10-21
What are the permissions set to? Try:

```
sudo chmod ugo+x /usr/bin/compiz*
```

---

### Post by emigrant on 2009-10-21
have i done correctly?

```

arshad@arshad-desktop:~$ sudo chmod ugo+x /usr/bin/compiz*
[sudo] password for emigrant: 
emigrant@emigrant-desktop:~$ 
emigrant@emigrant-desktop:~$ 

```

what i mean by 'visual effects' is the default one wich comes with ubuntu; not the compiz one.

---

