---
title: "need permission"
date: 2006-05-18
forum: General Help
---

### Post by shredfitz on 2006-05-18
okay i need permissions to write to the /lib folder .  all of the folders in the file system have locks on them .  I need to unlock these.  Have sought the information and once again, it doesn't work for me.  Please be nice.  I am trying with this ish.

---

### Post by dirwood on 2006-05-18
sudo [whatever command you want to perform]

it will prompt for a password, just type your password in.

---

### Post by aysiu on 2006-05-18
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by abstracthumor on 2006-05-18
I was going to say sudo nautilus and then write

---

### Post by rcarring on 2006-05-19
sudo nautilus 

won't work, try creating a launcher with the command 

gksudo nautilus.

---

### Post by tonyr on 2006-05-19
[QUOTE=rcarring]sudo nautilus 

won't work, try creating a launcher with the command 

gksudo nautilus.[/QUOTE]

Why do you say that?  **sudo nautilus** worked just fine for me (Dapper 6.06 updated
about 1/2 hour ago.    **gksudo nautilus** also seems to work, but for me produces
a warning:
> 
(nautilus:5702): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


[COLOR="DarkRed"]EDIT: Is it different in Breezy 5.10?[/COLOR]

---

### Post by rcarring on 2006-05-19
sudo nautilus in Breezy will most of the time fire up a message saying that display window cannot open, as presumably the user typed in sudo nautilus at a terminal prompt.

gksudo nautilus is used where you want to create a desktop launcher to run nautilus as superuser .

what happens is the gksudo bit tells the OS to open a dialog box and get a password for root access.

Ubuntu doesnt have a root login, just sudo or sudo su - to run as "root".

Hope that helps.

gksudo works in both Breezy and Dapper.

---

