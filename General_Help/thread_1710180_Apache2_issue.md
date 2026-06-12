---
title: "Apache2 issue"
date: 2011-03-19
forum: General Help
---

### Post by CNM on 2011-03-19
Hello ,

i am doing a simple :
sudo /etc/init.d/apache2 restart

and getting this error :
[COLOR=Red]
apache2: Syntax error on line 230 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/000-default: No such file or directory
Action 'configtest' failed.
The Apache error log may have more information.
...fail![/COLOR]

i need help with this ASAP please

thanks

---

### Post by nv1us on 2011-03-19
this may be a dumb question, but can you verify that you created a symlink to that file from /etc/apache2/sites-available/default
[HTML]sudo ln -s /etc/apache2/sites-available/default /etc/apache2/sites-enabled/000-default[/HTML]

---

### Post by CNM on 2011-03-19
> **nv1us said:**
> this may be a dumb question, but can you verify that you created a symlink to that file from /etc/apache2/sites-available/default
[HTML]sudo ln -s /etc/apache2/sites-available/default /etc/apache2/sites-enabled/000-default[/HTML]


yeah it's already there ...
i already checked it before posting ...
any other idea ? :)

---

### Post by vivek.pandey on 2011-03-19
can you post the apache2.conf file here?

---

### Post by CNM on 2011-03-19
> **neo_aryan said:**
> can you post the apache2.conf file here?

actually i was in a hurry to fix it
so i did an apt remove with purge and reinstalled it
that solved it ...
i should have kept the old files for debugging purposes though ... the error seemed interesting :P lol

---

### Post by vivek.pandey on 2011-03-19
glad your problem is solved..better mark it solve anyways :-)

---

### Post by CNM on 2011-03-19
> **neo_aryan said:**
> glad your problem is solved..better mark it solve anyways :-)

Thanks :)
done :)

---

