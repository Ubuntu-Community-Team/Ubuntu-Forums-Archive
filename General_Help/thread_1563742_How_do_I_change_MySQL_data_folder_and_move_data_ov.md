---
title: "How do I change MySQL data folder and move data over on ubuntu 10.04?"
date: 2010-08-29
forum: General Help
---

### Post by chjustc on 2010-08-29
Hi there,

I install ubuntu 10.04 (64bit) on my desktop and try to move my existing MySQL data over.

I first install MySQL on the new machine, and it can start and stop fine. I decide to change the data folder from the default (/var/lib/mysql) to /home/MyAccount/MySQLdata and move my existing MySQL data to that directory.

Because I used to use MySQL on my laptop and set the data directory on a USB drive, my existing data is on the USB drive. I connect the USB drive to the desktop and copy the old data folder to the new data folder by using
```
sudo rsync -av /media/USBdrive/MySQLdata/ /home/MyAccount/MySQLdata
```
Then, I change the ownership of the new folder
```
sudo chown mysql:mysql /home/MyAccount/MySQLdata
```
Next, I edit /etc/mysql/my.conf and update the "datadir" to my new directory. I also update /etc/apparmor.d/usr.sbin.mysql so that lines with /var/lib/mysql are commented out and news lines with /home/MyAccount/MySQLdata are added. I reload the apparmor ```
sudo /etc/init.d/apparmor reload
``` However, when I try to start mysql with ```
sudo start mysql
``` it hangs. When I try ```
sudo mysqld
``` and connect to mysql ```
mysql -u root -p
``` it complains ```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
```

Do you have any idea what I need to test and/or do to fix this problem? Thanks.

Best,
Jia

---

