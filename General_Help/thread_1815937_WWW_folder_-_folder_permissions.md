---
title: "WWW folder - folder permissions"
date: 2011-08-01
forum: General Help
---

### Post by Guavatree on 2011-08-01
Hi,

Im a web developer who uses PHP. I have installed Apache, PHP and MySQL on my Ubuntu installation with the web root being  here:
/var/www/

So, I have a project that I now want to past into that folder to test it. When I try, I get the following error:
> 
The folder "assist2" cannot be copied because you do not have permissions to create it in the destination.


What Must I DO!

---

### Post by akakingess on 2011-08-01
I would run gksudo nautilus and copy your files into WWW as WWW is "system" file, it requires root or sudo access.

---

### Post by Jouke S on 2011-08-01
type 'sudo' before your command

---

### Post by Guavatree on 2011-08-01
Thank you for you replies. What I really would like to do, and I hope that this is possible, is edit the files from that location using Kommodo Edit.

Is that possible?

I wish their was a way of disabling the SUDO requirement. Im no the Pentagon :D

---

### Post by Wim Sturkenboom on 2011-08-01
You can make apache use a directory in your home directory; below a quote from another thread

> **volkswagner said:**
> You also have the option to move your web directory to your home directory and edit the /etc/apache2/sites-available/hostfilename to point to that location.  


And maybe my setup as posted in [http://ubuntuforums.org/showpost.php?p=11100956&postcount=2](http://ubuntuforums.org/showpost.php?p=11100956&postcount=2) will be useful as you will more than likely maintain multiple sites. You need to setup virtual hosts for that, by the way

---

### Post by bodhi.zazen on 2011-08-01
> **akakingess said:**
> I would run gksudo nautilus and copy your files into WWW as WWW is "system" file, it requires root or sudo access.

That only works if you are running X and gnome on the server.

Use sudo ;)

---

### Post by pqwoerituytrueiwoq on 2011-08-01
I would just change the permissions on the folder
sudo chown -R $USER:$USER /var/www/*
if your page edits or saves files www-data will need write permissions

---

### Post by akakingess on 2011-08-01
> **bodhi.zazen said:**
> That only works if you are running X and gnome on the server.

Use sudo ;)

I was assuming since he had stated that he had installed Apache, etc. on his Ubuntu installation and wasn't familiar with sudo, that he had not installed the server edition.

---

