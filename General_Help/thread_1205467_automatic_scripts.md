---
title: "automatic scripts"
date: 2009-07-06
forum: General Help
---

### Post by R.E.A.D on 2009-07-06
hello evryone does anyone know how to implement scripts directly into the OS so that they run when needed automatically or at startup/loging in or could you at least point me in the right direction

---

### Post by paradox_qu on 2009-07-06
To run scripts at start up you can put them in /etc/rc.local

if you want to run scripts at certain times then do a search on cron

---

### Post by R.E.A.D on 2009-07-06
thanks,but how would you write a script and make an icon link to run that script or make it so that when the user clicks this or does that the script is automatically run so the user dosent even have to think about it, it just happens

---

### Post by paradox_qu on 2009-07-06
if you put a script in /etc/rc.local it will run automatically when the computer starts up.  If you put it in cron it will run at the specified time on the specified day automaticaly.  A user will have to do nothing, these will run automaticly.

remember you have to give the scrpit exacuatble permissions.  You can put it in the users path and he/she can run it via command line or you can make a symlink and put the symlink where you want that the user can click on.  That way the script runs when the user click on it.

---

### Post by kpkeerthi on 2009-07-06
> **R.E.A.D said:**
> thanks,but how would you write a script and make an icon link to run that script or make it so that when the user clicks this or does that the script is automatically run so the user dosent even have to think about it, it just happens

Right-click on your desktop and explore the options
For a menu item, Right-click on Applications on the top panel, choose Edit menus and explore the options.

---

### Post by R.E.A.D on 2009-07-06
no i mean for system designing so that when the iso is finished it is all implemented so that when you install it all of these things are already done and the system is all set up and if you design it to be so everything works out of the box pretty much

---

