---
title: "!!!!   HELP !!! Error with MYSQL Apache2- file owner"
date: 2011-02-18
forum: General Help
---

### Post by spindler on 2011-02-18
Hello

I have made a big mistake. and I hope someone can help. 

I have a website on my Ubuntu server ( Version 10.04 with a LMAP) I am having problems accessing my site remotely in order to upload pictures to the website.  This has been a low priority but long term problem.... I have posted questions about this issue on this forum without resolving my problem...so i have been holding off fixing it until I have time......now I have time...  So I thought it might be worth while to try something different to fix my problem.   I thought I might create a directory in the VAR folder to uploads files to directly.....In order to do this I thought first I need to change the owner of the VAR director...so this is what I did.


SUDO chown -R root:user var


of course once I did this my website went down!             I saw the following error message using Firefox.

_ERROR establishing a database connection   _

Seeing this issue.  I attempted to correct my mistake and changed the owner back to  root:root using the following:

sudo chown -R  root:root VAR

I thought this would set everything back to normal....However, It did not.             I then attempted the following:

sudo /etc/init.d/apache2 reload
sudo /etc/init.d/apache2 restart

This did not reconnect the database.....So I restarted the server.   During the restart I received two new errors.
[U]
Could not update ICEauthority file var/lib/gdm/iceauthority[/U]

_There is a problem with the configuration server.  (/user/lib/libgconf204/gconf-sanity-check-2 exited with status 256)_

Now..... I know I screwed up.... What I need is some help to get myself unscrewed up.      My website is currently down.  I need it back up ASAP.

Please.... any help would be great?

Spindler
:confused:

---

### Post by spindler on 2011-02-18
So I have some new information.  I attempted and failed to log into MySQL database.  I have several user names including ROOT, User and other users dedicated for individual websites and all of them do not allow me access to the MySQL database.    

I am logging in using the http control panel.  [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

1. How do I reset the MySQL user name and password? 
2. Is there a way I can reboot MySQL?
Is there a config file I can edit to reset the password?

Have help would be greatly appreciated. 

Thanks,

Spindler

---

