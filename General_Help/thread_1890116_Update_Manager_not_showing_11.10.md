---
title: "Update Manager not showing 11.10"
date: 2011-12-02
forum: General Help
---

### Post by mooseman123 on 2011-12-02
Hi all,

I had received the prompt to update to Ubuntu 11.10, but I cancelled it when my battery was almost dead. ](*,) Now I cannot seem to be able to reach a window for updating. Any ideas, or should I just go through terminal? :confused:

Thanks!

---

### Post by ExileAmongYou on 2011-12-02
You might be able to finish the upgrade by typing 
```
sudo apt-get dist-upgrade
``` in a terminal. Be careful to check that it's upgrading to 11.10, not 12.04 though.

Also, I'm not meaning to rub salt in your wounds, but I'm pretty sure the upgrader gives you a pretty strong suggestion to plug in your AC before you start so that your batteries don't run out halfway through. It might be worthwhile following that advice in future.

---

### Post by mooseman123 on 2011-12-02
I'll try this and post again. I started it when I thought I had my adapted with me, but my connection was slower than I thought, too.

UPDATE:
Just tried this; the terminal only gave this:
> admin@ubuntu:~$ sudo apt-get dist-upgrade
[sudo] password for admin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by ExileAmongYou on 2011-12-02
Sorry, after a quick bit of googling, I've discovered that apt-get dist-upgrade doesn't do what I thought it did. What you want should be this:
```
sudo do-release-upgrade -m desktop
```

---

### Post by oldtimer7777 on 2011-12-02
> **mooseman123 said:**
> Hi all,

I had received the prompt to update to Ubuntu 11.10, but I cancelled it when my battery was almost dead. ](*,) Now I cannot seem to be able to reach a window for updating. Any ideas, or should I just go through terminal? :confused:

Thanks!

I've had nothing but trouble trying to upgrade from one version to the next in Ubuntu. 

I have found it is always easier to just reinstall the latest version you wish to install from a USB Live Stick of Ubuntu.   The instructions on how to create a live stick of Ubuntu are on the Ubuntu.com web site... (option 2)

And here is a guide to get that installed correctly:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by mooseman123 on 2011-12-03
Excited to say I am writing this message from oneiric ocelot. :D

Thanks for your help. :)

---

