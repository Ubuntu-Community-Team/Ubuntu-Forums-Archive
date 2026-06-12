---
title: "MySQL missing root user"
date: 2011-03-12
forum: General Help
---

### Post by fishwebby on 2011-03-12
Hello,

I'm having a strange time trying to install MySQL on my Ubuntu server - using 

```
sudo apt-get install mysql-server

```

it installs ok, and prompts me for the root password during the install, but then when I try to use the client with

```
mysql -uroot -p

```

It denies me access. If I run using --skip-grant-tables (as described [here]("http://ubuntuforums.org/showpost.php?p=6432028&postcount=7")) it shows there is no root user.

Things I've tried:

- removing the install completely, using sudo apt-get remove mysql-server --purge, then sudo apt-get autoremove --purge
- installing using aptitude instead of apt-get
- sudo /usr/bin/mysql_install_db (this says "Installation of system tables failed!")
- sudo dpkg-reconfigure mysql-server-5.1 (this prompts for a root user password)
- lots of combinations of the above with reboots inbetween...

So it seems that MySQL installs ok but doesn't create the root user for some reason.

Anyone any ideas?

---

### Post by fishwebby on 2011-03-16
Seems I've managed to fix this, so I'm posting it here in case it's helpful (I don't know if the lack of replies means that no-one else has had this problem, but anyway...)

From reading install logs I think it might have had something to do with permissions on the /tmp folder. These were set to 700, and I think the mysql user needs access to write there, so I set it to (what I believe are the correct permissions):

```
sudo chmod 1777 /tmp
```

That didn't work straight away, even when purging the installation and trying again - it seems that even using apt-get remove with the --purge flag doesn't remove everything, so I used

```
sudo updatedb
```

followed by

```
locate mysql
```

to find all the remnants of the mysql install so I could remove them. Then a

```
sudo apt-get install mysql-server
```

worked as it should, giving me a nice root user.

(You should then run mysql_secure_installation but that's another post...)

Cheers
Dave

---

