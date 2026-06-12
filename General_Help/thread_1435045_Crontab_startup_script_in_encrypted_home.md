---
title: "Crontab startup script in encrypted home"
date: 2010-03-21
forum: General Help
---

### Post by audi4780 on 2010-03-21
Hi Everyone,

I have a sh script that is in my home directory that I would like to run at startup. I have added it to the crontab @reboot and it will not run. I installed Ubuntu 9.10 Server x64 with encrypted home directories.

If i move the script into another folder outside my home directory then it will run. I am guessing the home directory is not mounted unless I login???? For security purposes I would like to keep the script it in my home directory.

Does anyone have any ideas how i can achieve this??

Thanks!

---

### Post by lightspd on 2010-03-21
Have you tried specifying the user(you), in the crontab entry?  I don't use crontab much, so just a thought.

---

### Post by geirha on 2010-03-21
If you add it to startup applications (System -> Preferences -> Startup Applications) it will run when you log in.

---

