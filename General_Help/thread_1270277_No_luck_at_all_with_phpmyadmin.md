---
title: "No luck at all with phpmyadmin"
date: 2009-09-19
forum: General Help
---

### Post by Inge Jones on 2009-09-19
I had it installed once, but it was not allowing me to create a table. It didn't let me log in as the user who had the right permissions on MySQL (denied such a user existed) and if I logged in as the phpmyadmin main user I apparently had no privileges on MySQL. So I decided to uninstall both of them and start again - this time using exactly the same name and password for the admin of both.
 
MySQL is now happy and accepting logging in on that name and password, but I cannot reinstall phpmyadmin. I get stuff like: 
 
 
>  
*** WARNING: ucf was run from a maintainer script that uses debconf, but
the script did not pass --debconf-ok to ucf. The maintainer
script should be fixed to not stop debconf before calling ucf,
and pass it this parameter. For now, ucf will revert to using
old-style, non-debconf prompting. Ugh!
Please inform the package maintainer about this problem.
Replacing config file /etc/phpmyadmin/config-db.php with new version
dbconfig-common: flushing administrative password
apache2: Syntax error on line 278 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
...fail!
invoke-rc.d: initscript apache2, action "reload" failed.
 

 
Is there nothing like cpanel that we can use with Ubuntu? I am using the commandline only at the moment, via Putty as it is not convenient to use the console (no spare IO devices and the linux box is in another room).

---

### Post by quixote on 2009-09-20
By cpanel equivalent, do you mean something like synaptic in this case?  That allows one-click installs of phpmyadmin, etc.  (System > Administration > Synaptic)

It looks like phpmyadmin didn't uninstall properly.  You can try "Fix broken packages" in Synaptic, but the command line way is usually more effective for this.

[COLOR="Blue"]sudo dpkg --remove phpmyadmin[/COLOR] uninstalls but keeps config files.
[COLOR="Blue"]sudo dpkg --purge phpmyadmin[/COLOR] also removes config files.  This is probably the one you want, since it looks like the configuration is also bad.

If neither of those work, the big guns are```
sudo dpkg --force-overwrite --install phpmyadmin-3.2.2
```BUT I don't know the exact version number, and I think for this option to work you have to specify the exact package.  Not sure.  Maybe somebody else knows?

Dpkg is the actual program that synaptic is a front end for.  If removing or purging was successful, then you could use synaptic to install if you wanted.

---

