---
title: "installing and uninstalling mysql"
date: 2010-12-23
forum: General Help
---

### Post by andrea_bio on 2010-12-23
Hello
 
I installed mysql on Ubuntu linux with the command apt-get install mysql-server. How do i competely uninstall it? Please bear in mind i am a linux beginner with only command line access via putty. :)
 
Is there a way when i install the server to configure the server options (e.g. where the data directory is). I know how to change this once installed but i was wondering if there was a way to do it during the installation for ease. All i remember from the installation procedure is that you can set the root password.
 
thanks

---

### Post by Wtower on 2010-12-23
To uninstall try
```
sudo apt-get remove mysql-server
```

To uninstall and completely remove configuration files try
```
sudo apt-get purge mysql-server
```

---

### Post by Habitual on 2010-12-23
sudo apt-get install -y debconf-utils

Create a ~/mysql.preseed file with these entries:
mysql-server mysql-server/root_password password **YourPassword**
mysql-server mysql-server/root_password_again password **YourPassword**
mysql-server mysql-server/start_on_boot boolean true

cat ~/mysql.preseed | sudo debconf-set-selections
sudo apt-get install -y mysql-server

done.

---

### Post by Habitual on 2010-12-23
Can the the data directory be changed **during** an install?
If not, preseeding with a file won't work to set that option.

You probably already know this, but here it is for everyone's benefit. :)

**How to preseed a MySQL installation**
sudo apt-get install -y debconf-utils

run sudo debconf-get-selections | grep mysql (This works ONLY if it's been installed at least once)
and search for the variables you want changed during an install, (I don't know if the install directory is in this list, it's NOT on my install)

Create a ~/mysql.preseed file with these entries:
mysql-server mysql-server/root_password password **YourPassword**
mysql-server mysql-server/root_password_again password **YourPassword**
mysql-server mysql-server/start_on_boot boolean true

cat ~/mysql.preseed | sudo debconf-set-selections
sudo apt-get install -y mysql-server

done.

If the data dir can be specified during installation then debconf-get-selections may be able to tell you this and you can add that to the preseed file too.

HTH.

---

