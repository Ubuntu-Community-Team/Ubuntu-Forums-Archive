---
title: "Help changing permissions for /www"
date: 2010-06-22
forum: General Help
---

### Post by Phyxiis on 2010-06-22
Alright so my problem is that I somehow can't seem to change my permissions in the /var/www folder.

What I do is open terminal and sudo su and then enter nautilus as root and go to /var/www and right click /www because I want everything in that folder to be able to be edited by me. I try changing everything on the properties window so I can do this but the folder inside /www won't change (ie /www/phpbb3 permissions won't change)

I want every single file in /var/www to be changed so I can edit anything I want in there. Is there a way to do this?

-Thanks

---

### Post by Serpher on 2010-06-22
Changing the permissions of your www directory is a really bad idea and opens up your website to a whole bunch of threads. To operate a web server in linux you really should be comfortable with the command line, at least enough to navigate directories and open things in gedit. If you really want to change that though use the following command:

```
sudo chown <username> /var/www/
```

eg:

```
sudo chown matt /var/www/
```

---

### Post by Phyxiis on 2010-06-23
This doesn't really allow me to edit everything. Inside the phpbb3 folder there are still locked folders which I obviously can't edit.

What kind of threats are we talking about here? If you could lead me in the direction to an answer on the threats that would be fabulous

---

### Post by Phyxiis on 2010-06-23
Also, how would I take away the previous permissions?

---

### Post by slooksterpsv on 2010-06-23
sudo chown -R <username> /var/www

That does it recursively for all folders and files to make you the owner.

If you have certain group permissions applied and your part of that group you could also do:

sudo chgrp -R <group> /var/www

Then give the group full access:

chown -R g=wrx /var/www

Permissions are so fun =D

---

