---
title: "Unable to login new user"
date: 2012-05-18
forum: General Help
---

### Post by gabrielkhiu on 2012-05-18
I'am using VMWare workstation to run ubuntu. I am unable to login to the a new user i created (siwtching user in graphical environment)

In my admin shell , I am only able to c my admin account with (users) command. I used to be able to see both my admin and newuser with that command. the /home/newuser directory is also not available.

I tried poweroff my ubuntu and restart many times but its of no use. Please help guys. Thanks

---

### Post by goodvikings on 2012-05-18
post output of 

cat /etc/passwd | grep <new user name>

and 

sudo cat /etc/shadow | grep <new user name>

---

### Post by gabrielkhiu on 2012-05-18
lol i dunno how to attach the pic.

here is what it says : newuser: x :1001:1001::/home/newuser:bin/sh for the first command.

here is what it says: newuser: (the encrypted pass):15478:0:99999:7::: for the second command

---

### Post by gabrielkhiu on 2012-05-18
lol i dunno how to attach the pic.

here is what it says : newuser: x :1001:1001::/home/newuser:bin/sh for the first command.

here is what it says: newuser: (the encrypted pass):15478:0:99999:7::: for the second command

---

### Post by goodvikings on 2012-05-18
How did you create the new user?

The last bit of the first commands output should be /bin/sh as opposed to bin/sh

also, if the home directory doesn't exist that will give you problems. Create the directory (/home/newuser according to /etc/passwd) give it the right ownership and privs, try again.

Cheers

Ramo

---

