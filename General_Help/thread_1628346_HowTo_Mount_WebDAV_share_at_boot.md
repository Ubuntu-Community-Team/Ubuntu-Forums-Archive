---
title: "HowTo Mount WebDAV share at boot"
date: 2010-11-22
forum: General Help
---

### Post by kg4wih on 2010-11-22
**I couldn't find a how to anywhere on this, so here's mine.**
*sudo apt-get install fusedav*

**Make a mount location, chown the directory, give yourself permissions.**
[I]sudo mkdir /your/mount/location
sudo chown yourusername:yourusername /your/mount/location
sudo chmod 770 /your/mount/location[/I]

**I put my script in /etc/init.d. I'm sure you could put it anywhere though.**

**Paste the following in the file.**
[I]#! /bin/sh
/bin/su -c "fusedav -u USER -p PASSWORD [http://yourserver/yourdir](http://yourserver/yourdir) /your/mount/location &" yourusername [/I]

**Make the permissions readable only by root, because it has your password in plain text.**
[I]sudo chown root:root /etc/init.d/scriptname
sudo chmod 600 /etc/init.d/scriptname[/I]
[B]
Make it executable.[/B]
*sudo chmod +x /etc/init.d/scriptname*

**Make it run at boot.**
*sudo update-rc.d /etc/init.d/scriptname defaults*

**Reboot and use.**

---

### Post by andylb on 2011-01-20
I tried this and when running the *sudo update-rc.d /etc/init.d/scriptname defaults, *i get "file does not exist"

---

### Post by mbeltoft on 2011-04-07
How do I reverse the setup if I don't want to mount my webDav at boot anymore?

---

### Post by jrob09BHS on 2012-03-30
just remove /etc/init.d/ and just type in update-rc.d scriptname

---

### Post by thugwithyoyo on 2012-07-16
I followed your directions above and am able to mount my webdav file share on startup.  Works great.  Thanks for the post!

---

### Post by thugwithyoyo on 2012-07-16
I followed your instructions and am able to mount my WebDAV fileshare on startup.  Many thanks for your post.

---

