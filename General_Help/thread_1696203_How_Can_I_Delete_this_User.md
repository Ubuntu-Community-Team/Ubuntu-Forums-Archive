---
title: "How Can I Delete this User?"
date: 2011-02-27
forum: General Help
---

### Post by user68 on 2011-02-27
I created a user using the following script in a guide to installing Asterisk, but now I cannot delete the user. (I've tried to uninstall Asterisk)

adduser asterisk --disabled-password --no-create-home --gecos "asterisk PBX user"
adduser www-data asterisk

cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf_orig
sed -i 's/^\(User\|Group\).*/\1 asterisk/' /etc/apache2/apache2.conf

sed -i '1 {s/\<sh\>/bash/}' /usr/sbin/safe_asterisk

I'm guessing maybe this might be causing a problem? I have no idea how to change it:

mysqladmin -u root -p${MYSQL_ROOT_PW} create asterisk
mysqladmin -u root -p${MYSQL_ROOT_PW} create asteriskcdrdb
mysql -u root -p${MYSQL_ROOT_PW} asterisk < SQL/newinstall.sql
mysql -u root -p${MYSQL_ROOT_PW} asteriskcdrdb < SQL/cdr_mysql_table.sql
mysql -u root -p${MYSQL_ROOT_PW} <<-END_PRIVS
GRANT ALL PRIVILEGES ON asterisk.* TO asteriskuser@localhost IDENTIFIED BY "${ASTERISK_DB_PW}";
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asteriskuser@localhost IDENTIFIED BY "${ASTERISK_DB_PW}";

---

### Post by doas777 on 2011-02-27
may be a stupid question, but have you tried 
```
sudo userdel asterisk
```?

in terms of mysql, here is some info on the DROP USER statement:
[http://dev.mysql.com/doc/refman/5.0/en/drop-user.html](http://dev.mysql.com/doc/refman/5.0/en/drop-user.html)

also is the username asterisk or asteriskuser? seems like your output conflicts on that point.

whats the output of 
```
cat /etc/passwd
```

---

