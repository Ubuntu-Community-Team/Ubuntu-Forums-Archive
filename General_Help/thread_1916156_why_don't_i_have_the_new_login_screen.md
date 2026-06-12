---
title: "why don't i have the new login screen?"
date: 2012-01-27
forum: General Help
---

### Post by rajohns08 on 2012-01-27
i have 11.10 but...

this is what my login screen looks like:
[http://img189.imageshack.us/img189/2950/ubuntu1010loginscreen.jpg](http://img189.imageshack.us/img189/2950/ubuntu1010loginscreen.jpg)

this is what i want it to look like:
[http://img268.imageshack.us/img268/889/ubuntu1110lightdmlogins.png](http://img268.imageshack.us/img268/889/ubuntu1110lightdmlogins.png)

i have tried:
[http://freshtutorial.com/change-background-login-screen-ubuntu-1110/](http://freshtutorial.com/change-background-login-screen-ubuntu-1110/)

but it didn't work

how do i accomplish this?

---

### Post by hwttdz on 2012-01-27
alt+ctrl+f2
login as you
sudo service stop gdm
sudo service stop xdm
sudo service start lightdm

How's that?

---

### Post by rajohns08 on 2012-01-27
> **hwttdz said:**
> alt+ctrl+f2
login as you
sudo service stop gdm
sudo service stop xdm
sudo service start lightdm

How's that?

did you mean:
```
sudo service gdm stop
sudo service lightdm start
```

that worked but didn't save when i restarted. how do i save that configuration so it will be like that everytime i restart?

---

### Post by rajohns08 on 2012-01-27
nvm here is answer:

[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

once lightdm is being used you can change background image with ubuntu tweak

---

