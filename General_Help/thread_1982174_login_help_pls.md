---
title: "login help pls"
date: 2012-05-18
forum: General Help
---

### Post by gabrielkhiu on 2012-05-18
I'am using VMWare workstation to run ubuntu. I am unable to login to the a new user i created (siwtching user in graphical environment)

In my admin shell , I am only able to c my admin account with (users) command. I used to be able to see both my admin and newuser with that command. the /home/newuser directory is also not available.

I tried poweroff my ubuntu and restart many times but its of no use. Please help guys. Thanks

after using the cat /etc/passwd and sudo cat /etc/shadow command

newuser: x :1001:1001::/home/newuser:bin/sh 
newuser: (the encrypted pass):15478:0:99999:7:::

---

### Post by 2F4U on 2012-05-18
If the /home/newuser folder is not available, that is probably the reason why you cannot login to that user. You could try to create the folder manually and make the account the owner of the folder.

---

### Post by gabrielkhiu on 2012-05-18
omg i was figuring out how to solve it the whole day yesterday! thank you very much!! :)

---

