---
title: "How to launch a graphical application using gnome -schedule"
date: 2010-09-08
forum: General Help
---

### Post by neoargon on 2010-09-08
How to launch a graphical application using gnome-schedule ?

I got some tutorials about cron after googling . But I couldn't understand the stuff about Screen number 

As an example, please tell what should be typed in "Task:"  to launch say, nautilus

---

### Post by Bonster on 2010-09-08
export DISPLAY=:0 /usr/bin/nautilus

or u might have to put it into a script

---

### Post by neoargon on 2010-09-09
> **Bonster said:**
> export DISPLAY=:0 /usr/bin/nautilus

or u might have to put it into a script
That doesn't work

---

### Post by dcstar on 2010-09-09
> **Bonster said:**
> export DISPLAY=:0 /usr/bin/nautilus

or u might have to put it into a script
If you are going to give code to people that obviously have no idea what they are doing then at least test it so you can find you mistake!
```
export DISPLAY=:0; /usr/bin/nautilus
```

---

