---
title: "Problems with phpmyadmin and mysql"
date: 2006-06-06
forum: General Help
---

### Post by blakegrover on 2006-06-06
I was going through a howto on how to get mythtv setup and I installed phpmyadmin and mysql-server and I was going in to change the password for root on the mysql database server but I accidentlly deleted the root account from the mysql database.  At the time I thought maybe I just messed up the phpmyadmin setup and not the root account of the phpmyadmin so I deleted all the config files in the /etc/phpmyadmin and the directory and removed it and then re installed in through apt-get thinking it would recreate all the config files again and maybe it would fix it.  ](*,) Silly me found out that it doesn't recreate them and it knew I deleted them and they used to be there.  So then my phpmyadmin site started complaining that it did not have any config files.  Then I tried loggin in to the mysql database on the console and I found out that the root user was deleted.  So this time I removed the mysql-server and say it still left my ruined mysql database files in /var/lib/mysql/ so I deleted the directory and then tried to reinstall mysql-server again and with no suprise this time I saw that it knew I deleted the databse files and it did not create them for me again.](*,)  So Does anyone know how I can at least get my msql working back to the default settings?  I really feel stupid since at work I maintain a mysql database server and I am used to using the console to do all my changes.  Any help would be appreciated.

Blake

---

### Post by ifokkema on 2006-06-06
[QUOTE=blakegrover]I was going through a howto on how to get mythtv setup and I installed phpmyadmin and mysql-server and I was going in to change the password for root on the mysql database server but I accidentlly deleted the root account from the mysql database.  At the time I thought maybe I just messed up the phpmyadmin setup and not the root account of the phpmyadmin so I deleted all the config files in the /etc/phpmyadmin and the directory and removed it and then re installed in through apt-get thinking it would recreate all the config files again and maybe it would fix it.  ](*,) Silly me found out that it doesn't recreate them and it knew I deleted them and they used to be there.  So then my phpmyadmin site started complaining that it did not have any config files.  Then I tried loggin in to the mysql database on the console and I found out that the root user was deleted.  So this time I removed the mysql-server and say it still left my ruined mysql database files in /var/lib/mysql/ so I deleted the directory and then tried to reinstall mysql-server again and with no suprise this time I saw that it knew I deleted the databse files and it did not create them for me again.](*,)  So Does anyone know how I can at least get my msql working back to the default settings?  I really feel stupid since at work I maintain a mysql database server and I am used to using the console to do all my changes.  Any help would be appreciated.

Blake[/QUOTE]

Sounds to me you need to run mysql_install_db :)
I think that should set you up nicely.

Ivo

---

### Post by blakegrover on 2006-06-06
Thanks that got my mysql server up and working again.  :)

---

### Post by cyracks on 2006-06-06
Next time you need to completely delete the package do:
sudo apt-get remove --purge package_name
synaptic: "Mark for complete removal"

---

