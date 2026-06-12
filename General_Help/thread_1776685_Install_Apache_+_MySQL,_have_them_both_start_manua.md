---
title: "Install Apache + MySQL, have them both start manually"
date: 2011-06-06
forum: General Help
---

### Post by Kenneth Fox on 2011-06-06
I'm aware you can install Apache, PHP, MySQL with tasksel, but because messing with runlevels seems to be pretty useless nowadays, I was wondering what would be the best way to install Apache and MySQL and have it only start manually?

In the interest of having an informative topic, here is the command to install Apache, PHP, and MySQL.

```
sudo apt-get install tasksel && sudo tasksel install lamp-server
```

I am running 10.10, by the way.

---

### Post by lykwydchykyn on 2011-06-06
```

sudo update-rc.d apache2 disable
sudo update-rc.d mysql-server disable

```

That should do it.

---

### Post by Kenneth Fox on 2011-06-08
When you enter in the mysql one, I get this error on 10.10.

```
$ sudo update-rc.d mysql disable
update-rc.d: warning: /etc/init.d/mysql missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/mysql do not exist
```

I can confirm MySQL is in fact running at the moment installed through tasksel.

---

### Post by lykwydchykyn on 2011-06-08
I thought update-rc.d was upstart-savvy, but apparently not.

I don't know if there's an official way to do it, but you could edit /etc/init/mysql.conf and comment out these lines:
```

start on (net-device-up
          and local-filesystems
          and runlevel [2345])

```

---

