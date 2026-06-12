---
title: "forgot ubuntu 10.10 username."
date: 2010-10-24
forum: General Help
---

### Post by ckop11 on 2010-10-24
Okay so i installed ubuntu 10.10 a week or two ago. (total ubuntu newb)

The problem i have is i installed kubuntu via synap a few days ago then i did a restart. to see what it was like.

i go to log in and the login screen is different. and it doesn't have the user-name that i used saved. so i don't remember my user-name for ubunutu. i tryed everything i could think of but i don't know it. I know my Password. but not the user-name.   so i cant log in.

 anyone know anything i can do?


Or how can i see the user-name i used? without logging in? in Terminal maybe??

thank you everyone in advanced.

---

### Post by sisco311 on 2010-10-24
Hi and welcome to the forums!

Boot into recovery mode and run:
```
ls /home
```
or
```
awk -F: '{if ($3>999) print $1}' /etc/passwd
```
to find your username.

For details, see [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by ckop11 on 2010-10-24
Thanks! im now on the ubuntu that i couldnt get into. thankyou.

---

### Post by sisco311 on 2010-10-24
> **ckop11 said:**
> Thanks! im now on the ubuntu that i couldnt get into. thankyou.

You are welcome!

BTW, if you want to change the default display manager, open a terminal (Applications -> Accessories -> Terminal) and run:
```
sudo dpkg-reconfigure -fgnome gdm
```
and follow the instructions.

---

