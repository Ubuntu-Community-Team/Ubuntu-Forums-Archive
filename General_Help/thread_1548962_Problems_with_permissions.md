---
title: "Problems with permissions"
date: 2010-08-09
forum: General Help
---

### Post by tarun_pai on 2010-08-09
Hey, I'm using Ubuntu 9.10, I downloaded netbeans 6.9 IDE for some PHP development, The problem is that, when i try saving my file in the /var/www directory it says > permission denied as a result I can't really test my php files 'coz they wont run, help!!

---

### Post by elliotn on 2010-08-09
Alt+F2 then type gksudo nautilus

---

### Post by rizzeh on 2010-08-09
you need to use sudo to copy to /var/www.
Either do it through the CL:
```
sudo cp file.txt /var/www/
```

or use nautilus as root to copy:
```
gksudo nautilus
```

First method is prefered. :)

---

