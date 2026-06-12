---
title: "Another startup script problem 9.04"
date: 2009-07-10
forum: General Help
---

### Post by thefatmoop on 2009-07-10
I just updated to 9.04, and normally i have a conky script thats located in /home/conky.sh and it is just: 

```
#!/bin/bash
sleep 15
conky -c /home/main.conkyrc&
exit
```

need it to sleep 15 since sometimes compiz messes up if conky loads prior. 


i use to just add /home/conky.sh to sessions. Did the exact same thing as before doesnt work. 

sessions is now called "startup applications"? still looks same. both are executable, i also tried putting it in init.d... not working 

anyone know?

---

### Post by Peter09 on 2009-07-10
Hi,
just to check, should the path not be

> ......./home/<your userid>/........

---

### Post by thefatmoop on 2009-07-10
yeah... if i do it like that the conky configs dont load properly

---

### Post by Peter09 on 2009-07-10
I would have though that putting it in init.d would not work because that is run at boot time, before you login, and therefore you would have no session for conky to attach to.

---

### Post by thefatmoop on 2009-07-10
yea didn't work. i'm just confused why it's not loading from startup applications... i've done it same way on all other systems no problem

---

### Post by Peter09 on 2009-07-10
Have you looked into the system logs to see if there are any error messages.

---

### Post by thefatmoop on 2009-07-10
no i'll look at it tomorrow. If i sudo ./conky.sh it loads fine

---

### Post by Peter09 on 2009-07-10
Just looked at the permissions for /home. Its owned by root and does not have write permissions for a normal user (at least on my system). I would put the script in your home directory and work it from there.

---

### Post by thefatmoop on 2009-07-10
yea just needed some sleep. since i added it there using sudo nautilus then i moved it to home directory using sudo in terminal... the owner was root which didn't allow me to even read it? 

had to go into admin nautilus and change the owner

---

