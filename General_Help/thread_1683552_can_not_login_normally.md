---
title: "can not login normally"
date: 2011-02-07
forum: General Help
---

### Post by johnny19931993 on 2011-02-07
I installed ubuntu 10.10 using wubi on my netbook a few days ago. There wasn't any problems until yesterday when i tried to login, the normal logic screen didn't show up. Instead, it shows a black background and white text prompting for username and password. After i logged in with that it just keeps prompting like the terminal. I tried ctrl + alt + f7 and it didn't work. I think i changed the xorg.conf file the last time i login and it might be the reason why this happened. But i can't change the file back to normal cuz it says access denied when i tried to edit it even though i'm using an admin account.

---

### Post by johnny19931993 on 2011-02-07
bump

---

### Post by zander1013 on 2011-02-07
> **johnny19931993 said:**
> bump

i am observing a similar problem. it seems (at least on my system) that if you wait about 90sec or 2min. that the regular login screen will appear.

from there i have set System>Admin>Login Screen to "Login as <user>" automatically. this works for now but i am waiting for an answer to make it show the login screen right away when it boots.

---

### Post by zander1013 on 2011-02-07
actually what i suggested does not help. i still have to wait for the login screen to start.

---

### Post by johnny19931993 on 2011-02-08
bump

---

### Post by bcbc on 2011-02-09
> **johnny19931993 said:**
> I installed ubuntu 10.10 using wubi on my netbook a few days ago. There wasn't any problems until yesterday when i tried to login, the normal logic screen didn't show up. Instead, it shows a black background and white text prompting for username and password. After i logged in with that it just keeps prompting like the terminal. I tried ctrl + alt + f7 and it didn't work. I think i changed the xorg.conf file the last time i login and it might be the reason why this happened. But i can't change the file back to normal cuz it says access denied when i tried to edit it even though i'm using an admin account.
Rename the xorg.conf, then start gnome desktop manager
```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.bu
sudo service gdm start
```

Or edit it with:
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by johnny19931993 on 2011-02-09
> **bcbc said:**
> Rename the xorg.conf, then start gnome desktop manager
```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.bu
sudo service gdm start
```Or edit it with:
```
sudo nano /etc/X11/xorg.conf
```

thanks very much
i can login normally now =)

---

### Post by fgking on 2011-02-10
I can now login in the safe mode. I think the reason why I could not get access to genome is because graphic mode demands more memory. I hoe this helps someone.

---

