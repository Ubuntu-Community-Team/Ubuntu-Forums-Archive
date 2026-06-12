---
title: "Ubuntu 11.10 gawk problem"
date: 2011-11-25
forum: General Help
---

### Post by izuz on 2011-11-25
Hi all,

I just installed ubuntu 11.10 64-bits desktop on virtualbox, and everything is working very smoothly. however one single problem thats annoying. Every time (literally every time) I start a terminal. I get the following message first:
The program 'gawk' is currently not installed.  You can install it by typing:
sudo apt-get install gawk

What might be causing, this?

Thank you,

---

### Post by Vaphell on 2011-11-25
probably your ~/.bashrc (or some other config file for shell) uses gawk which is not installed and the shell complains about it, just like if you typed gawk in terminal by hand.

---

### Post by izuz on 2011-11-27
I haven't touched ~/.bashrch (or any config file), expect the /etc/profile where i added JAVA_HOME and GRAILS_HOME environment variables. i don't understand where is this problem comming from.

---

### Post by Vaphell on 2011-11-27
either way initialization of bash shell requires gawk somewhere
In virtualbox i could reproduce this message by adding gawk to the .bashrc

try grepping the bash related files in ~ and in /etc for gawk... or just install gawk and be over with it ;-)

---

### Post by oldtimer7777 on 2011-11-27
> **Vaphell said:**
> either way initialization of bash shell requires gawk somewhere
In virtualbox i could reproduce this message by adding gawk to the .bashrc

try grepping the bash related files in ~ and in /etc for gawk... or just install gawk and be over with it ;-)

And if you have a fresh install it is good to review the checklist first after you have it installed:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

