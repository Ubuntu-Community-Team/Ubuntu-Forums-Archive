---
title: "gnome-session-fallback wont stay"
date: 2011-10-25
forum: General Help
---

### Post by ddr3XD on 2011-10-25
So i installed gnome-session-fallback on Ubuntu 11.10 using this code:
```
sudo apt-get install gnome-session-fallback
```Logged out, selected GNOME Classic. It worked but whenever i restart it goes back to the default desktop. How can i make it keep the fallback gnome desktop?

---

### Post by oldtimer7777 on 2011-10-25
Here is how:

[https://debianhelp.wordpress.com/2011/10/14/how-to-change-default-session-in-ubuntu-11-10/](https://debianhelp.wordpress.com/2011/10/14/how-to-change-default-session-in-ubuntu-11-10/)

> **ddr3XD said:**
> So i installed gnome-session-fallback on Ubuntu 11.10 using this code:
```
sudo apt-get install gnome-session-fallback
```Logged out, selected GNOME Classic. It worked but whenever i restart it goes back to the default desktop. How can i make it keep the fallback gnome desktop?

---

### Post by ddr3XD on 2011-10-25
> **oldtimer7777 said:**
> Here is how:

[https://debianhelp.wordpress.com/2011/10/14/how-to-change-default-session-in-ubuntu-11-10/](https://debianhelp.wordpress.com/2011/10/14/how-to-change-default-session-in-ubuntu-11-10/)

Hey thanks, LightDM now remembers what desktop I selected but if I re-enable Auto-login it always logs in to the default desktop. Does this meen I cant use auto-login anymore?

---

### Post by oldtimer7777 on 2011-10-25
> **ddr3XD said:**
> Hey thanks, LightDM now remembers what desktop I selected but if I re-enable Auto-login it always logs in to the default desktop. Does this meen I cant use auto-login anymore?

No, it means you will have to change the configuration settings from the command line. Open up gedit and edit the file that contains the settings for LightDM.  I don't recommend it if you are new to Ubuntu.  But instructions exists if you google them.

---

### Post by ddr3XD on 2011-10-26
**[COLOR=Red]Thank You[/COLOR]** oldtimer7777 :D

got it done by using:
```
sudo gedit /etc/lightdm/lightdm.conf
```Then change "user-session=ubuntu" to:
```
user-session=[COLOR=Red]gnome-classic[/COLOR]
```

---

