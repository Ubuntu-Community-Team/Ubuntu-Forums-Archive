---
title: "Fail to change MySQL data directory"
date: 2009-08-25
forum: General Help
---

### Post by chjustc on 2009-08-25
Hi there,

I am using kubuntu 8.04.

I followed this link [http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive](http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive) to change the data directory of MySQL.

After stopping MySQL
```
sudo /etc/init.d/mysql stop
```
I make a new directory,
```
sudo mkdir /media/disk/MySQL_data
```
then change the ownership of new directory,
```
sudo chown mysql:mysql /media/disk/MySQL_data
```
and copy all data to the new directory,
```
cp -r -p /var/lib/mysql/* /media/disk/MySQL_data/
```
I then edit /etc/mysql/my.conf and update the "datadir" line to my new directory. I also update /etc/apparmor.d/usr.sbin.mysql so that news lines with /var/lib/mysql replaced by /media/disk/MySQL_data are added.

After
```
sudo /etc/init.d/apparmor reload
```
I try ```
sudo /etc/init.d/mysql start
```.

I got  ```
* Starting MySQL database server mysqld                                        [fail]
```

While getting this error, I see new ibdata1, ib_logfile0, and ib_logfile1 created in my new data directory. 

If I change the "datadir" line in /etc/mysql/my.conf back to the original one, I can start MySQL successfully.

I think I have done everything needed to change MySQL data directory. Why am I still getting this error? Thanks.

---

