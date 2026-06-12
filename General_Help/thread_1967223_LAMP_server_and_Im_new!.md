---
title: "LAMP server and Im new!"
date: 2012-04-27
forum: General Help
---

### Post by TheNardCake on 2012-04-27
Hi!  Im new to ubuntu really!  Anyways Installed ubuntu on my laptop to run a temporary webserver on it.  I installed the LAMP (Linux Apache MySQL Php) server.  It's all working fine, but I was trying to put my website on the server by dragging all my folders and stuff into /var/www and it said I don't have permission.  Im very confused because 1. Im the only user. 2. Im the admin the one who installed it and ya...?
Very confused any help is very much appreciated!
(was this the right place to post...?)

---

### Post by sundays211 on 2012-04-27
By default, only the root user has write access to /var/www.
Is it possible to point lamp to read from a different directory? Much easier if you have it reading from a subfolder in your home directory

---

### Post by TheNardCake on 2012-04-27
> **sundays211 said:**
> By default, only the root user has write access to /var/www.
Is it possible to point lamp to read from a different directory? Much easier if you have it reading from a subfolder in your home directory
Woah im brand new what does that mean? :D  Im litterally in the file browser going to that directory.
Edit: Ok so if I figure out how to do that it should work?  Well thats just another thing to do... :D

---

### Post by sundays211 on 2012-04-27
You can do one of two things:
1) Change the permissions of the /var/www directory (by typing ```
sudo chmod a+w /var/www
``` into the terminal)

2) Point the server to a different directory. This you can do by editing the apache2 config file:
```
sudo gedit /etc/apache2/sites-available/default
``` and changing ```
DocumentRoot /var/www
``` and ```
<Directory /var/www/>
``` to your desired folder name.

for example, if you create a folder in your home directory called 'www', then you would change it to ```
/home/[your username]/www
```

---

### Post by TheNardCake on 2012-04-27
> **sundays211 said:**
> You can do one of two things:
1) Change the permissions of the /var/www directory (by typing ```
sudo chmod a+w /var/www
``` into the terminal)

2) Point the server to a different directory. This you can do by editing the apache2 config file:
```
sudo gedit /etc/apache2/sites-available/default
``` and changing ```
DocumentRoot /var/www
``` and ```
<Directory /var/www/>
``` to your desired folder name.

for example, if you create a folder in your home directory called 'www', then you would change it to ```
/home/[your username]/www
```
Thank you so much!

---

### Post by sundays211 on 2012-04-27
No problem, though if you have a problem in the future and you still don't know a lot about Ubuntu, you might like to try the "[**Absolute Beginner Talk**]("http://ubuntuforums.org/forumdisplay.php?f=326")" forum ;)

---

### Post by fragos on 2012-04-28
What I do is to put links in /var/www that point to the sites stored in my /home folder. To make the links you can Alt+F2 gksudo nautilus /var/www. The folder is now opened by root so you can easily create the links.

---

