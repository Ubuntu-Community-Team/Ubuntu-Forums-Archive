---
title: "ubuntu 10.4 LTS login"
date: 2010-09-04
forum: General Help
---

### Post by cactus17 on 2010-09-04
I installed Ubuntu 10.4.1 LTS version. I installed livetex and then i updated /etc/profile file and /etc/enviroment. 
In both files i wrote
PATH="bla"
MANPATH="bla"
 
Then i did logout. Next time when i trying to login and write password, i am geturning to the same login screen. There is no "authentication failure" message.
If i trying to login with wrong username, then i have authentication failure.
 
Now, the problem is, that every time i do login with correct username and correct password, press enter, then i get to the same login screen.
 
SOS! HELP!

---

### Post by cactus17 on 2010-09-04
I solved it. I logged in command prompt, and deleted PATH variable from /etc/profile.
The problem was that the PATH that i added there, deleted path to /usr/bin so the system could not log in.

---

