---
title: "Permission denied while copying fies to var/www"
date: 2010-03-16
forum: General Help
---

### Post by brainbugg on 2010-03-16
I just installed Apache2, PHP5 and MySQL on my Ubuntu 9.10.
I have about 200+ .php format files of my site (including index.php) which I need to copy to var/www.

But the permission is denied. Please help!

---

### Post by J V on 2010-03-16
edit your sites-available to send the directory to another folder (somewhere in your home)

---

### Post by uylug on 2010-03-16
> **J V said:**
> edit your sites-available to send the directory to another folder (somewhere in your home)

Exactly. When creating sites I set the document root to a /home/xxx/xxx folder.

You can edit your default settings by doing a :
```

gksudo gedit /etc/apache2/sites-available/default
```

And changing every "/var/www" to a folder under your home folder.

You can also force copy files to /var/www by running nautilus as root:
```

gksudo nautilus /var/www
```

---

### Post by mikemelen on 2010-03-16
Type below command in terminal and try to copy

#sudo su

Give your password, then try to copy

or

#sudo nautilus

---

### Post by uylug on 2010-03-16
> **mikemelen said:**
> Type below command in terminal and try to copy

#sudo su

Give your password, then try to copy

or

#sudo nautilus

Thanks but that is exactly what I was trying to avoid because I am expecting to run program(s) with my user and I want them to access my data, not my system :P

---

### Post by jsriz on 2010-03-16
alt+F2 run gksudo nautilus 
copy your files to /var/www 
then rt click /var/www and go to permissions tab and set read and write permissions as required(i.e for the user as whom you will be logged on as when you are using your apps).

---

