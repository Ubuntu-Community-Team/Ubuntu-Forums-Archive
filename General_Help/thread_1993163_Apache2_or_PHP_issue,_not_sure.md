---
title: "Apache2 or PHP issue, not sure"
date: 2012-06-01
forum: General Help
---

### Post by OldManRiver on 2012-06-01
All,

Can anyone tell me why one of my machines, when going to:

localhost

pops up the dialog box seen in attachment.  I looked in both the php.ini and the apache2 config files and can not find anything cluing me in on this.

Thanks!

OMR

---

### Post by OldManRiver on 2012-06-02
All,

Can I get some help here?

OMR

---

### Post by dragonfly41 on 2012-06-02
I would just hazard a guess that the file in docroot (/var/www/   ?)  has no php extension ?

What do you see when you choose "open"?

Can you run phpinfo.php?

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #3 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

### Post by greenpeace on 2012-06-11
Hi, 

Can you run phpinfo.php, as asked by dragonfly41?  

Does Apache know to serve it as a PHP file?  Did you enable the php module in Apache?

```
sudo a2enmod php5
```

(full installation guide for LAMP servers here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) )

---

### Post by maverickaddicted on 2012-06-11
> **greenpeace said:**
> Hi, 

Can you run phpinfo.php, as asked by dragonfly41?  

Does Apache know to serve it as a PHP file?  Did you enable the php module in Apache?

```
sudo a2enmod php5
```

(full installation guide for LAMP servers here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) )

Also install -

```
sudo apt-get install libapache2-mod-php5
```

Then restart your apache, clear your browser cache and reopen the
page.

---

### Post by OldManRiver on 2012-10-10
All,

Had to add the line:
```
DirectoryIndex index.php index.html
```
to the /etc/apache2/apache2.conf file

No longer get that dialog now!

Closing this thread!

Cheers!

OMR

---

