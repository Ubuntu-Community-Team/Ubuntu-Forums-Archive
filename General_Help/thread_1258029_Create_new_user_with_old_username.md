---
title: "Create new user with old username"
date: 2009-09-04
forum: General Help
---

### Post by JackWarrior on 2009-09-04
Greetings,

   1st message on the ubuntu forums...

I don't know how to solve the following:
- yesterday i created a user "guest". due to some issues on gdm to connect under this user, i had to delete it (the classic way: system / admin / user and groups etc.) and i logged as root to delete the home/guest folder
- today i figured out how to solve my problems at gdm
- so i wanted to recreate the user "guest" (the classic way again: system / admin / user and groups etc.)

Ubuntu is telling me the user already exists and can consequently not accept the username "guest" again. but the thing is that i can not find any trace of "guest" anywhere...

what do i have to do to be able to re-use "guest" as user name ?

thanks !

---

### Post by bear24rw on 2009-09-04
is it still in /etc/shadow?

---

### Post by geirha on 2009-09-04
It's possible the guest group is still around; when you create a user, a group by the same name is created and set as the user's primary group. If there is already a group by the same name as the user you want to create, it will prohibit you from creating it.

Does any of these commands give any output?
```
getent passwd guest
getent group guest
```

---

### Post by JackWarrior on 2009-09-04
to geihra:
   the 1st command gives nothing
   the 2nd: **guest:x:1003:**

 to bear24rw: no

edit: you guys pointed the solution for me: i had a group called "user". just removed it and i am now able to use guest again as user name! cheers

---

