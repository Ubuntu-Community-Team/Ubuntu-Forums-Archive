---
title: "PHPmyAdmin 403 Error"
date: 2011-12-16
forum: General Help
---

### Post by OldManRiver on 2011-12-16
All,

I recently installed PHPExcel on my 10.04 U-Box and now I get a 403 error, from my [http://localhost/phpmyadmin](http://localhost/phpmyadmin) page.

Went out changed all the permission, etc. even ran remove=>purge + reboot + install and nothing changed.

Could use a little troubleshooting help.

Thanks!

OMR

---

### Post by fdrake on 2011-12-16
in the phpmyadmin folder do you have the index.php file? also do you have php enabled? "sudo a2enmod php5"

---

### Post by OldManRiver on 2011-12-16
fdrake,

Yup & Yup

Actually writing PHP script to port to Excel, but need to load DB and can't.

OMR

---

### Post by fdrake on 2011-12-16
> **OldManRiver said:**
> fdrake,

Yup & Yup

Actually writing PHP script to port to Excel, but need to load DB and can't.

OMR
did you try to connect to mysql with the terminal?

---

### Post by OldManRiver on 2011-12-16
fdrake,

Appears MySQL is down or dead.  Will look at it and get back to you.

Cheers!

OMR

---

### Post by fdrake on 2011-12-16
maybe that was the original issue? let us know...

---

### Post by OldManRiver on 2011-12-16
fdrake,

Could not get in MySQL from cmd line, so checked install and was fine.  Then opened the MySQL Admin GUI tool, got in fine, but fould all user permissions denied, so fixing!

Let you know where I get!

OMR

---

### Post by OldManRiver on 2011-12-16
fdrake,

K!  Got the permissions restore and passwords reset and now get in at cmd line, but still getting 403 so suspect the config file.  Trying to remember it's name!

OMR

---

### Post by fdrake on 2011-12-16
you mean  ./phpMyAdmin/phpdoctor.ini ? or you mean the /etc/php.ini?
to find all the conf files do
```
locate php | grep ini
```

also question: do your php scripts run in the server? if 'yes' then the problem is in phpmyadmin only...

unfortunately I have never used before "PHPExcel" so I am not sure exactly what could have happened..

---

### Post by OldManRiver on 2011-12-16
fdrake,

Naw!  It's the config.inc.php file in the phpmyadmin that has the login crap on windows, but it pulls in config.db.php in Linux where the DB UID/PWD and DB to use are all stored.

Found them now just getting the passwords right!

Cheers!

OMR

---

### Post by OldManRiver on 2011-12-16
fdrake,

Well permissions right, config right, etc and still 403 error.

Clearing cache next.

OMR

---

### Post by fdrake on 2011-12-16
what about reinstalling phpmyadmin? in case cache does not work ..

oh I forgot you already did that.. hmmm

---

### Post by OldManRiver on 2011-12-16
Cache cleared no change

---

### Post by OldManRiver on 2011-12-16
FD,

Had already done a purge re-install, so not sure if I would gain anything.

OMR

---

### Post by fdrake on 2011-12-16
localhost is active, and the php scripts they do run , right?

---

### Post by OldManRiver on 2011-12-16
fdrake,

One final check of /usr/share/phpmyadmin and found the permissions at 766.  I had set to 755 before, so reset and now all works.

Gotta have that X in users group or doesn't run!

Thanks for the help!

Cheers!

OMR

---

### Post by fdrake on 2011-12-16
i am glad now it's working . i wonder how the installation of phpexcel has influenced the permissions ...?
> **OldManRiver said:**
> 
Thanks for the help!

I did nothing! You did everything by yourself.. I was here mostly for MORAL SUPPORT :)

---

### Post by OldManRiver on 2012-02-17
> **fdrake said:**
> I did nothing! You did everything by yourself.. I was here mostly for MORAL SUPPORT :)
fdrake,

Sometimes moral support and/or a sounding board is all that is needed!

Thanks!

---

