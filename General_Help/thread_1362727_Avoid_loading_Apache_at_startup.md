---
title: "Avoid loading Apache at startup"
date: 2009-12-23
forum: General Help
---

### Post by Nonno Bassotto on 2009-12-23
Hello, I'd like to install Apache+PHP+MySql on my netbook, to do some web development while traveling. The problem is that I don't want all these services to be loaded at startup. In normal situations I don't need them and I'd rather save some battery.

How can I disable them at startup? And how do I load them when needed? For Apache it is
```

sudo /etc/init.d/apache2 start

```
but I'm not sure about MySql.

---

### Post by mihamil on 2009-12-23
Install Bum (boot up manager) and run that application.  From there you can determine everything that starts during bootup.

The commands to start apache and mysql are 
sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysqld start

---

### Post by junapp on 2009-12-23
or look into update-rc.d

```
sudo update-rc.d apache2 remove
```maybe wait until someone more knowledgeable seconds that.

BAD ADVICE - DISREGARD.

---

### Post by Nonno Bassotto on 2009-12-23
Thank you very much!

---

