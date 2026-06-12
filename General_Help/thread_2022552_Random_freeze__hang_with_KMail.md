---
title: "Random freeze / hang with KMail"
date: 2012-07-11
forum: General Help
---

### Post by oygle on 2012-07-11
Running 10.04 and KMail 1.13.5 and KDE 4.4.5 , and get a random freeze, usually when trying to send emails.

Any clues please ?

The Akonadi server had errors in the log file, here is part of it ..

> 
Test 4:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file &apos;<a href='/home/username/.local/share/akonadi/db_data/mysql.err'>/home/username/.local/share/akonadi/db_data/mysql.err</a>&apos; contains errors.

File content of '/home/username/.local/share/akonadi/db_data/mysql.err':
120711 19:04:29 [Note] Plugin 'FEDERATED' is disabled.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
120711 19:04:29  InnoDB: Retrying to lock the first data file
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.


---

