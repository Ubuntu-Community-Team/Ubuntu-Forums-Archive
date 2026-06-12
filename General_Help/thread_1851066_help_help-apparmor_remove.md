---
title: "help help-apparmor remove"
date: 2011-09-27
forum: General Help
---

### Post by gabikilalala on 2011-09-27
hello everyone,
well i need some help.i removed apparmor for installing an ubuntu server 11.04 32 bit with the "perfect server-ispconfig3" guide.the link is:
[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3)
So after removing it i wasnt able to install packages or update or upgrading.
it gives me erroes.well i am trying for weeks, and i really need your help.
thank you very very much:p

---

### Post by Gregorybekkers on 2011-09-27
What are the errors?

---

### Post by gabikilalala on 2011-09-27
well i did what the guide says...i ran in terminal

 /etc/init.d/apparmor stop
 update-rc.d -f apparmor remove
 apt-get remove apparmor apparmor-utils

 in root mode..

 everything goes well and then i ran 

 apt-get install ntp ntpdate.
 and it gets Errors..E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
after that i ran again the steps but in the vm the fist step for me was to remove apparmor and i found out that it can update.
so the second step i made was change the shel from dash to bash.according to the guide.so what causes that?
 well sorry if i dont describe this well./
 thank you

---

### Post by gabikilalala on 2011-09-27
oh,after changing the shell i wasnt able to update again...
thank you

---

