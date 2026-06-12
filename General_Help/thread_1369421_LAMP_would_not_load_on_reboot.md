---
title: "LAMP would not load on reboot"
date: 2009-12-31
forum: General Help
---

### Post by Kdar on 2009-12-31
If I reboot or turn on computer after swometime, LAMP doesn't seem to load.

I used tutorial from this site:
[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)

How do I make LAMP start on each boot?

---

### Post by dcstar on 2010-01-01
> **Kdar said:**
> If I reboot or turn on computer after swometime, LAMP doesn't seem to load.

I used tutorial from this site:
[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)

How do I make LAMP start on each boot?

Don't use the network-manager package, instead use something that sets up networking without requiring a login (like gnome-network-admin).

---

### Post by john newbuntu on 2010-01-01
First make sure that the files /etc/init.d/mysql and /etc/init.d/apache2 exist and is owned by root with permission 755.  If they do exist, then type these commands from a terminal:

```
sudo update-rc.d apache2 start 91 2 3 4 5 . stop 09 0 1 6 .
sudo update-rc.d mysql start 19 2 3 4 5 . stop 21 0 1 6 .
```

---

### Post by Kdar on 2010-01-01
> **john newbuntu said:**
> First make sure that the files /etc/init.d/mysql and /etc/init.d/apache2 exist and is owned by root with permission 755.  If they do exist, then type these commands from a terminal:

```
sudo update-rc.d apache2 start 91 2 3 4 5 . stop 09 0 1 6 .
sudo update-rc.d mysql start 19 2 3 4 5 . stop 21 0 1 6 .
```

They both exists and have 755 permission and owned by root.

But when I go to [http://localhost](http://localhost) or to my drupal site installed on there, it doesn't work.

It only able to work after I enter those two commands:
```
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart

```

So those two are not get loaded when I log into my Ubuntu on boot?

------
> **dcstar said:**
> Don't use the network-manager package, instead use something that sets up networking without requiring a login (like gnome-network-admin).

Sorry. But how do I do that?

---

### Post by dcstar on 2010-01-01
> **Kdar said:**
> 
........
Sorry. But how do I do that?

Install the other package, then uninstall network-manager and set up the networking with the other one.

---

