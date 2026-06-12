---
title: "Call an another script in a bootup script"
date: 2010-02-02
forum: General Help
---

### Post by bakegoodz on 2010-02-02
Is there a special way to call a script in pre login enviroment. I have a script that runs before login I have init script /etc/rc2.d/S99-startup it calls main.sh, that runs fine, but in main.sh also calls aux.sh, the command is just /scripts/aux.sh  It gets executed when main.sh is ran after loging in, but when I boot up the computer main.sh runs but it won't call aux.sh. It would really be a mess to combine them, both scripts have several function calls, and I couldn't keep them all straight in my head if there all in one file.

Anyways is there another way I should try calling the aux.sh script? 

There must some environment variable difference or something messing it up, I don't know

---

### Post by Barriehie on 2010-02-02
Can you post the involved scripts please?

Barrie

---

### Post by bakegoodz on 2010-02-03
I got the thought maybe it needs all absolute paths
I tried this and it worked

/bin/bash /scripts/main.sh

---

