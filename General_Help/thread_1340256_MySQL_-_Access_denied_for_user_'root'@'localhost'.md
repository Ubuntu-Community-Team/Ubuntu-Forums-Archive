---
title: "MySQL - Access denied for user 'root'@'localhost'"
date: 2009-11-28
forum: General Help
---

### Post by DannyG on 2009-11-28
I'm having trouble with MySQL with which I am pulling out my hair.

For some reason, I cannot get into MySQL, at all. I am installing MySQL through Aptitude, during which it prompts me to enter my desired MySQL root password. However, after installation, I can't access it!

I have uninstalled and reinstalled MySQL, reformatted the box, even started MySQL with the --skip-grant-options to reset the root user password but no matter what I try I am always denied access.

```
alpha:~# mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
alpha:~#
```

```
alpha:~# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
alpha:~#
```

```
alpha:~# mysqladmin -u root password 'newpass'  
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
alpha:~#
```

I've tried it with the plainest of passwords to make sure it wasn't me screwing up the password, no luck.

Can anyone explain whats going on here? Why can't I get into MySQL?

P.S, mysql is definitely running!

---

### Post by Virtual Liberty on 2009-11-28
```
mysql -h localhost -u root -p
[COLOR="Gray"]-- enter password --[/COLOR]
```

If it fails, try [COLOR="DimGray"]mysql-admin[/COLOR] package.

---

### Post by DannyG on 2009-11-28
Thanks for the response.

> **Virtual Liberty said:**
> ```
mysql -h localhost -u root -p
[COLOR="Gray"]-- enter password --[/COLOR]
```

```
alpha:~# mysql -h localhost -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
alpha:~#
```

> **Virtual Liberty said:**
> If it fails, try [COLOR="DimGray"]mysql-admin[/COLOR] package.

Isn't that just a GUI frontend? That is useless if I can't actually gain access to the server...

---

### Post by Virtual Liberty on 2009-11-28
> **DannyG said:**
> 
Isn't that just a GUI frontend? That is useless if I can't actually gain access to the server...

The only useless thing would be to sit there and watch at how it rejects your password. Just saying from my personal experience - had a similar case when I couldn't authenticate myself through the command line but everything worked just fine through the GUI ( mysql-admin ).

---

### Post by DannyG on 2009-11-28
> **Virtual Liberty said:**
> The only useless thing would be to sit there and watch at how it rejects your password. Just saying from my personal experience - had a similar case when I couldn't authenticate myself through the command line but everything worked just fine through the GUI ( mysql-admin ).

Unfortunately this is running through SSH so a GUI is a little out of the question, short of installing a desktop environment and VNC'ing in.

Even if it did allow me access through a GUI, that still doesn't solve the problem when none of my applications can gain access to the server...

---

### Post by pi4r0n on 2009-11-28
I have been having this issue for the last 1 year on my local machine. 

I have ready and tried 100s different tutorials and I still can not fuc.. figured out how to fix it :(

---

### Post by DannyG on 2009-11-28
I've also tried to comment out

```
#bind-address = 127.0.0.1
```

so it'll listen on all interfaces, no luck.

---

### Post by Virtual Liberty on 2009-11-28
Can you show us the output of the following command ?

```
netstat -l
```

---

### Post by DannyG on 2009-11-28
> **Virtual Liberty said:**
> Can you show us the output of the following command ?

```
netstat -l
```

Sure.

```
alpha:~# netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:mysql                 *:*                     LISTEN     
tcp6       0      0 [::]:www                [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     15299    /var/run/mysqld/mysqld.sock
alpha:~#
```

Also, like I said, I can start mysqld in safe mode with the --skip-grant-tables flag and I can get in fine, I used this to try and reset the password but even after I came back out I still couldn't get in with the new password.

---

### Post by DannyG on 2009-11-28
When I access MySQL with the --skip-grant-tables option, and do a

```
SELECT * FROM mysql.users
```

I get the following output:

```
mysql> select * from user;
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| Host      | User             | Password                                  | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_slave_priv | Repl_client_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Create_user_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max_updates | max_connections | max_user_connections |
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| localhost | debian-sys-maint | *AD3DA746CE12EB25AA892D6BD4A65D450EC664AA | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | N                | N              | N                   | N                  | N                |          |            |             |              |             0 |           0 |               0 |                    0 | 
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
1 row in set (0.00 sec)

mysql>
```

Now, forgive my ignorance if I'm wrong here, but does this mean that the root user doesn't actually exist? Or, is the root user not shown here for security?

---

### Post by DannyG on 2009-11-28
It seems I was able to "fix" this problem by logging with --skip-grant-tables, and executing the following:

```
mysql> INSERT INTO user VALUES ('localhost','root',password('newpassword'),'Y','Y ','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y', 'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','' ,'','','',0,0,0,0); 
mysql> INSERT INTO user VALUES ('127.0.0.1','root',password('newpassword'),'Y','Y ','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y', 'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','' ,'','','',0,0,0,0);
```

This seems pretty far from ideal and will no doubt result in problems of some description on the future, so I'd like to actually get to the root (no pun intended) of the problem...

---

### Post by Virtual Liberty on 2009-11-28
> **DannyG said:**
> Now, forgive my ignorance if I'm wrong here, but does this mean that the root user doesn't actually exist? Or, is the root user not shown here for security?

```
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| Host      | User             | Password                                  | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_slave_priv | Repl_client_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Create_user_priv | Event_priv | Trigger_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max_updates | max_connections | max_user_connections |
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| localhost | root             | *189E2C3FBD73CDDEDB608D964307D7805BEFD34F | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
| mint      | root             | *189E2C3FBD73CDDEDB608D964307D7805BEFD34F | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
| 127.0.0.1 | root             | *189E2C3FBD73CDDEDB608D964307D7805BEFD34F | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
| localhost | debian-sys-maint | *A04AABE8B249F8877F4E924D86A5034645922E06 | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
```

As you see, if it's missing, no wonder it doesn't let you in.

---

### Post by DannyG on 2009-11-28
> **Virtual Liberty said:**
> ```
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| Host      | User             | Password                                  | Select_priv | Insert_priv | Update_priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | References_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_slave_priv | Repl_client_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Create_user_priv | Event_priv | Trigger_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max_updates | max_connections | max_user_connections |
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
| localhost | root             | *189E2C3FBD73CDDEDB608D964307D7805BEFD34F | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
| mint      | root             | *189E2C3FBD73CDDEDB608D964307D7805BEFD34F | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
| 127.0.0.1 | root             | *189E2C3FBD73CDDEDB608D964307D7805BEFD34F | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
| localhost | debian-sys-maint | *A04AABE8B249F8877F4E924D86A5034645922E06 | Y           | Y           | Y           | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y               | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y               | Y                | Y                | Y              | Y                   | Y                  | Y                | Y          | Y            |          |            |             |              |             0 |           0 |               0 |                    0 | 
+-----------+------------------+-------------------------------------------+-------------+-------------+-------------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+-----------------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-----------------+------------------+------------------+----------------+---------------------+--------------------+------------------+------------+--------------+----------+------------+-------------+--------------+---------------+-------------+-----------------+----------------------+
```

As you see, if it's missing, no wonder it doesn't let you in.

Yep, OK, so the problem is that for some reason the root user isn't being created. I'd like to find out why this is the case though...

Anyone got any ideas why the mysql-server installation isn't adding the root user?

---

