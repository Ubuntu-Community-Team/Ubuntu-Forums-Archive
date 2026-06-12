---
title: "I think my Apache, Mysql and PHPMyAdmin installs are screwed up, how can I uninstall?"
date: 2009-07-25
forum: General Help
---

### Post by sois on 2009-07-25
First of all, how can I make sure they are all installed correctly?
if they are not installed correctly, how can i remove/reinstall?

Thanks!

---

### Post by credobyte on 2009-07-25
> I think my Apache, Mysql and PHPMyAdmin installs are screwed up
Why do you think so ? What problems have you been experiencing ?

---

### Post by sois on 2009-07-25
I typed [http://localhost/](http://localhost/) and am getting nothing.
I have not done anything but install.  I should get some default page, shouldn't it?

---

### Post by credobyte on 2009-07-25
Install Apache & PHP:
```
sudo apt-get install apache2 php5 libapache2-mod-php5

```

Install MySQL ( server & administration utility ):
```
sudo apt-get install mysql-server mysql-admin
```

After installing all these packages, you should see a welcome page ( if not, try the same commands, except, replace *install* with *remove --purge* ).

---

### Post by sois on 2009-07-26
Setting up libapache2-mod-php5 (5.2.6.dfsg.1-3ubuntu4.1) ...
Your apache2 configuration is broken, so we're not restarting it for you.

---

### Post by credobyte on 2009-07-26
> **sois said:**
> Setting up libapache2-mod-php5 (5.2.6.dfsg.1-3ubuntu4.1) ...
Your apache2 configuration is broken, so we're not restarting it for you.
```

sudo apt-get remove --purge apache2 php5 libapache2-mod-php5
```

After removing your broken installation, try installing again.

---

