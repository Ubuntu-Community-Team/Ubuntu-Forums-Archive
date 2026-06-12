---
title: "Removing 'var/www' root Restrictions"
date: 2010-09-26
forum: General Help
---

### Post by inulled on 2010-09-26
I have an Apache, PureFTPd, PHP5, and MySQL server setup and running. I'm running several scripts that require folder access of "var/www" in order to accomplish the scripts duty. How do I remove and/or work around the security measure?

---

### Post by Tom of Helatrobus on 2010-09-26
[LIST=1]
[*]applications> terminal (to open terminal)
[*]cd /var     (to get to the right place)
[*]sudo chmod 777 -R www (to change the permissions)
[*]enter password
[*]ls -l (to check the permissions - permissions should read drwxrwxrwx all across)
[/LIST]
This works for me working with my LAMP, since other people are not accessing these files. But you can refine step 3 for more limited permissions.

---

### Post by inulled on 2010-09-26
Are these right? and thanks for the help....:
drwxr-xr-x  2 root root  4096 2010-09-26 07:40 backups
drwxr-xr-x 23 root root  4096 2010-09-26 11:53 cache
drwxrwxrwt  2 root root  4096 2010-09-24 07:35 crash
drwxr-xr-x  2 root root  4096 2010-04-29 08:26 games
drwxr-xr-x 70 root root  4096 2010-09-24 19:52 lib
drwxrwsr-x  2 root staff 4096 2010-04-23 06:11 local
drwxrwxrwt  4 root root    80 2010-09-26 12:03 lock
drwxr-xr-x 20 root root  4096 2010-09-26 12:02 log
drwxrwsr-x  2 root mail  4096 2010-04-29 08:17 mail
drwxr-xr-x  2 root root  4096 2010-04-29 08:17 opt
drwxr-xr-x 19 root root   840 2010-09-26 12:05 run
drwxr-xr-x  7 root root  4096 2010-09-22 02:04 spool
drwxrwxrwt  2 root root  4096 2010-09-26 12:08 tmp
drwxrwxrwx  3 root root  4096 2010-09-25 19:01 www

---

### Post by Tom of Helatrobus on 2010-09-26
Looks right as far as the www file is concerned. Since I only use localhost to test my php scripts the permissions can be wide open.

---

### Post by inulled on 2010-09-26
yeah... I usually only keep it within my LAN... so your right.... thanks :KS

---

### Post by psycho5 on 2010-09-26
Hey, there is an easy way to do this

First make a backup copy of the original file in apache2 

```

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite

```

Then edit your mysite file

```

sudo gedit /etc/apache2/sites-available/mysite

```

Change the DocumentRoot to point to the new location. For example, /home/user/public_html/

Change the Directory directive, replace <Directory /var/www/> to <Directory /home/user/public_html/>

Then finally, we disable the default and enable your "mysite"

```

sudo a2dissite default && sudo a2ensite mysite

```

first code is **a**pache**2** **dis**able **site** 
secondly enable yours **a**pache**2** **en**able **site**

Finally, restart apache2

```

sudo /etc/init.d/apache2 restart

```

Now you can edit your web folder at /home/user/public_html/ or whatever you decided to call it.

*edit*
Also, since it's in the home folder, you are the owner and you can set permissions to the entire folder

---

### Post by inulled on 2010-09-26
thanks

---

### Post by inulled on 2010-09-26
Hmm... just wondering... Does apache2 have its own group in the permissions settings?

---

