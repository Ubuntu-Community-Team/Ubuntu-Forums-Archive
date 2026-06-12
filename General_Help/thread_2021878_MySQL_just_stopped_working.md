---
title: "MySQL just stopped working"
date: 2012-07-09
forum: General Help
---

### Post by U2XS on 2012-07-09
I have a server which I use to test software.  Today I trying to log into PHPMyAdmin & it would not work.  I cannot log into MySQL.  Can't change the password.  

How would I go about reinstalling or reconfiguring the MySQL server?  I've tried uninstalling & reinstalling, but I always get errors.

---

### Post by U2XS on 2012-07-10
I have the following error message.  I checked the /usr/share/doc/mysql-server-5.5/README.Debian file, but my error is not related to the things it warns about.

```
Package configuration


 âââââââââââââââââââââââ¤ Configuring mysql-server-5.5 ââââââââââââââââââââââââ
 â                                                                           â
 â Unable to set password for the MySQL "root" user                          â
 â                                                                           â
 â An error occurred while setting the password for the MySQL                â
 â administrative user. This may have happened because the account already   â
 â has a password, or because of a communication problem with the MySQL      â
 â server.                                                                   â
 â                                                                           â
 â You should check the account's password after the package installation.   â
 â                                                                           â
 â Please read the /usr/share/doc/mysql-server-5.5/README.Debian file for    â
 â more information.                                                         â
 â                                                                           â
 â                                  <Ok>                                     â
 â                                                                           â
 âââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââââ





```

---

### Post by SeijiSensei on 2012-07-10
Did you try the methods described [here](https://help.ubuntu.com/community/MysqlPasswordReset)?

Once you get everything set up correctly, look into backing up the database with mysqldump nightly, if you don't do so already.  You might take a look at [this posting](http://ubuntuforums.org/showpost.php?p=10368151&postcount=3) for a sample script you can modify for your needs.

---

